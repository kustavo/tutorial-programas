# Dispositivos

## Barramentos PCI

Comando para mostrar informações dos barramentos pci e todos os dispositivos conectados a ele.

```bash
$ lspci
[-v] Modo detalhado nível 1
[-vv] Modo detalhado nível 2
[-vvv] Modo detalhado nível 3
```

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

## Referências
