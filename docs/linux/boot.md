# Boot

## Secure Boot

Alguns projetos podem exigir o uso de drivers de kernel personalizados que não são configurados de forma a funcionar com DKMS. Nesses casos, as pessoas devem usar as ferramentas incluídas no pacote `shim-signed`.

Use o seguinte comando para registrar uma chave existente no shim:

```bash
sudo update-secureboot-policy --enroll-key
```

- Se não existir nenhum MOK, o script sairá avisando que precisa criá-lo. Execute o comando abaixo:

    ```bash
    sudo update-secureboot-policy --new-key
    ```

    - Execute novamente o primeiro comando para registrar a chave.

- Se a chave já estiver cadastrada, o script sairá sem fazer nada.
- Se a chave existir, mas não for registrada, o usuário será solicitado a fornecer uma senha para usar após a reinicialização, para que a chave possa ser registrada.
    - Selecione a opção do menu `Enroll MOK`.

### Gerenciar opções de boot

As opções de boot são os arquivos `.conf` em `/boot/efi/loader/entries`.

Para colocar a opção do windows como padrão, por exemplo ou mudar o nome, é necessário criar um arquivo `.conf` contendo:

```ini
title Windows 10
# Nome que será exibido nas opções de boot
efi /EFI/Microsoft/Boot/bootmgfw.efi
# A partição `/boot` é só um ponto de montagem da partição `efi`
```

As configurações de boot estão em `/boot/efi/loader/loader.conf`:

```ini
default windows.conf
timeout 10
# Evitar que apareça opções de busca automática que não então em `/boot/efi/loader/entries`.
auto-entries 0
```

## Remover entradas do menu boot EFI

```bash
# Instalar
sudo apt install efibootmgr

# Ver a lista de entradas e os ids
sudo efibootmgr

# <id> é o id da entrada, ex: Boot0005 será "sudo efibootmgr -b 0005 -B"
sudo efibootmgr -b <id> -B
```

## Reparar o systemd-boot

```bash
sudo mount <particao-sistema> /mnt
sudo mount <particao-efi> /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/
sudo chroot /mnt
apt install --reinstall linux-generic linux-headers-generic
update-initramfs -c -k all
exit
sudo bootctl --path=/mnt/boot/efi install
```

## Dual boot EFI em disco diferente

Obs: Testado com Pop!_OS

Copiar o diretório EFI do Windows para dentro da EFI usada pelo linux.

Isso não altera nada no Windows, e o dualboot passa a funcionar imediatamente.

Passo 1 – Montar a EFI do Windows temporariamente. 
Nesse exemplo nvme0n1p1 é a partição EFI do windows.
```bash
sudo mkdir -p /mnt/efi-win
sudo mount /dev/nvme0n1p1 /mnt/efi-win
```

Passo 2 – Copiar o bootloader do Windows para a EFI do linux
```bash
sudo cp -r /mnt/efi-win/EFI/Microsoft /boot/efi/EFI/
```

Isso copiará a pasta Microsoft para dentro da EFI do linux, onde o systemd-boot realmente olha.

Passo 3 – Verificar se a pasta está lá
```bash
sudo ls /boot/efi/EFI
```

Você deve ver:

Boot  Microsoft  systemd  (e outros)

Passo 4 – Atualizar o systemd-boot

```bash
sudo bootctl update
```



### Modo de dormência

Comando para o sistema entrar em modo de dormência até o tempo determinado. Substitui o antigo comando **apmsleep**.

```bash
$ rtcwake
[-m] modo de desligamento.

    [standby] Modo suspender (standby). Economia de energia pequena.
    [mem] Suspender para a memória RAM. Todos os dispositivos são colocados em estado de baixo consumo, exceto a memória RAM, pois deve ficar ligada para evitar que as informações se percam. Economia de energia moderada.
    [disk] Suspender para o disco. Todo o conteúdo da memória RAM é salvo no disco, após isso o computador é desligado. Economia de energia alta.
    [off] Desligar o computador completamente. A BIOS precisa dar suporte.
    [no] Não suspende o computador, apenas define o horário para acordar.

[-v] Modo verboso. Mostrar detalhes.
[-t] Tempo absoluto.
[-s] Tempo em segundos.
[-l] Tempo informado é local, usado pelo sistema.
[-u] Tempo informado é o UTC.
```

Exemplos:

Suspender para o disco e acordar depois de duas horas.

```bash
rtcwake -m disk -s 7200
```

Desligar e acordar 19:00.

```bash
sudo rtcwake -m off -t 19:00
```

Não suspender ou desligar imediatamente, somente definir para acordar 8:00.

```bash
sudo rtcwake -m no -t 8:00
```

## Referências

- <https://wiki.ubuntu.com/UEFI/SecureBoot>
