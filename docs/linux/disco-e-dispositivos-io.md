# Disco e Dispositivos IO

## Teclado

### Mudança de Layout

Configuração do teclado em layout americano internacional.

```bash
setxkbmap -model pc104 -layout us_intl
```

## Bluetooth

### Problemas

Bluetooth não é habilitado.

```bash
sudo rmmod btusb
sudo modprobe btusb
```

Serviço não inicia automaticamente ao iniciar o sistema.

```bash
systemctl start bluetooth
systemctl enable bluetooth
```

## Disco

### Listar partições

Comando para listar as partições:

```bash
$ df
[-h] Grandeza informada baseada no tamanho.
```

### Badblocks

Comando para identificar e isolar badblocks:

```bash
$ badblocks
[-b] Especifica o tamanho de cada bloco.
[-s] Mostra o avanço do procedimento.
[-v] Verbose mode.
[-c] 10240 = Verifica 10 mil blocos de HD por vez.
[]
```

Exemplos:

Verificando apenas modo leitura.

```bash
sudo badblocks -sv -c 1024 /dev/sdaX
```

Verificando em modo leitura e escrita sem perda de dados.

```bash
sudo badblocks -nsv -c 10240 /dev/sdaX
```

Verificando em modo leitura e escrita com perda de dados.

```bash
sudo badblocks -wsv -c 10240 /dev/sdaX
```

## Barramentos PCI

Comando para mostrar informações dos barramentos pci e todos os dispositivos conectados a ele.

```bash
$ lspci
[-v] Modo detalhado nível 1
[-vv] Modo detalhado nível 2
[-vvv] Modo detalhado nível 3
```
