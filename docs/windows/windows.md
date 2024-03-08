# Windows

## Introdução

Microsoft Windows (ou simplesmente Windows) é uma família de sistemas operacionais desenvolvidos, comercializados e vendidos pela Microsoft.

## Boot

### Baixar ISO das últimas versões do Windows

<https://uupdump.net>

### Formatar e restaurar as partições EFI e MSR

```bash
diskpart
list disk
select disk <numero>           # disco que possui a partição EFI

list partition
select partition <numero>      # partição EFI
delete partition override
select partition <numero>      # partição MSR
delete partition override

list partition
select disk <numero>           # disco que possui a partição EFI
create partition efi size=700  # criar partição EFI com 700 MB

list partition
select partition <numero>      # partição EFI
format quick fs=fat32 label="EFI"
create partition msr size=20   # criar partição MSR com 700 MB

list partition
list vol
exit

bcdboot x:\windows            # x é a partição onde está o windows
```

### Restaurar a partição EFI

```bash
bcdboot x:\windows # x é a partição onde está o windows
```

## Rede

### Compartilhar Wifi de uma conexão cabeada

1. Abra as configurações da Internet, visualize as conexões de rede e altere opções do adaptador ("Change adapter options").

1. Selecione o adaptador Wifi e a Ethernet.

1. Clique com o botão direito e faça uma ponte de rede entre os dois ("network bridge").

1. Selecione a ponte de rede e a desative e exclua.

1. Clique com o botão direito no adaptador Wifi e clique em propriedades. Vá para a guia de compartilhamento e ative o compartilhamento novamente (certifique-se de que ambas as caixas estejam marcadas).

1. Vá para a guia de configurações e certifique-se de que todas as caixas estejam marcadas, exceto "Microsoft Network Adapter Multiplexor Protocol".

## WSL

WSL significa Windows Subsystem for Linux (ou Subsistema Linux para Windows) e permite que desenvolvedores executem um ambiente GNU/Linux diretamente no Windows, sem precisar de uma máquina virtual ou realizar um dual-boot.

### Instalação

```bash
# Instale o WSL e a distribuição Ubuntu padrão.
wsl --install

# Instalar uma distribuicao específica
wsl --install <nome-distribuicao>
```

### Listar distribuições

```bash
# Listar distribuições disponíveis
wsl --list --online

# Listar distribuições instaladas
wsl --list --verbose
```

### Definir distribuição padrão

```bash
wsl --set-default <nome-distribuicao>
```

### Executar uma distribuição específica

```bash
wsl --distribution <nome-distribuicao> --user <nome-usuario>
```

### Atualizar o WSL

```bash
wsl --update
```

### Verificar o status do WSL

```bash
wsl --status
```

### Verificar a versão do WSL

```bash
wsl --version
```

### Comando Help

```bash
wsl --help
```

### Execute como um usuário específico

```bash
wsl --user <username>
```

### Alterar o usuário padrão para uma distribuição

```bash
<nome-distribuicao> config --default-user <username>
```

### Shutdown

```bash
# Encerrar todas distros em execução e a máquna virtual
wsl --shutdown
```

### Terminate

```bash
# Encerrar apenas a distro indicada
wsl --terminate <nome-distribuicao>
```

### Identificar o endereço IP

```bash
wsl hostname -i
```

### Exportar uma distribuição

```bash
wsl --export <nome-distribuicao> <nome-arquivo-saida>

# Opções:
# --vhd: Exportação deve ser um arquivo .vhdx em vez de um arquivo .tar
```

### Importar uma distribuição

```bash
wsl --import <nome-distribuicao> <local-instalacao> <nome-arquivo>

# Opções:
# --vhd: Exportação deve ser um arquivo .vhdx em vez de um arquivo .tar
```

### Importar uma distribuição em vigor

```bash
# Importa o arquivo .vhdx especificado como uma nova distribuição.
# O disco rígido virtual deve ser formatado no tipo de sistema de arquivos ext4.
wsl --import-in-place <nome-distribuicao> <nome-arquivo>
```

### Cancelar o registro ou desinstalar uma distribuição do Linux

```bash
wsl --unregister <nome-distribuicao>
```

### Montar um disco ou dispositivo

```bash
wsl --mount <local-disco>

# Opções:
# --vhd: especifica que se refere a um disco rígido virtual.
# --name: nome personalizado para o ponto de montagem
# --type <Filesystem>: tipo do sistema de arquivos. Padrão será ext4.
```

### Desmontar discos

```bash
wsl --unmount <local-disco>
```

## Referências

- <https://learn.microsoft.com/pt-br/windows/wsl/basic-commands>
