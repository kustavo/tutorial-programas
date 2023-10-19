# VeraCrypt

## Introdução

VeraCrypt é um utilitário freeware (software livre),, usado para criptografia on-the-fly (OTFE). Ele pode criar um disco virtual criptografado dentro de um arquivo ou criptografar uma partição ou o dispositivo de armazenamento inteiro com autenticação pré-boot.

## Erros e soluções

### Codificação de caracteres no sistema de arquivos

Problemas ao exibir o nome dos arquivos com acentos.

**Solução**: Adicione o comando abaixo em "Preferences" -> "Mount Options" para aplicar em todos pontos de montagem.

```ini
iocharset=utf8
```

## Referências
