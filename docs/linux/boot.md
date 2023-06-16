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

## Remover entradas do menu boot EFI

```bash
# Instalar
sudo apt install efibootmgr

# Ver a lista de entradas e os ids
sudo efibootmgr

# <id> é o id da entrada, ex: Boot0005 será "sudo efibootmgr -b 0005 -B"
sudo efibootmgr -b <id> -B
```

## Referências

- <https://wiki.ubuntu.com/UEFI/SecureBoot>
