# configurando-shh
gerando chave SSH utilizando abordagem no contexto Windows / WSL / Linux.

```bash
# comando para gerar chave SSH
$ ssh-keygen

# fomulario de configuração - apresentado após a execução do comando ssh-keygen
# Generating public/private rsa key pair
# Todos os parâmetros são opcionais

$ Enter file in which to save the key (<current dir>):
$ Enter passphrase (empty for no passphrase):
$ Enter same passphrase again:
```
#
após a confirmação das opções são gerados os arquivos publico e privado, além da primeira sequencia de caracteres da chave SSH.

```bash
$ Your identification has been saved in C:\<current dir>/ .ssh/id_rsa.
$ Your identification has been saved in C:\<current dir>/ .ssh/id_rsa.pub.
$ The key fingerprint is:
$ SH256:OU/<sshkey_firgerprint>
```
# Copiando chave SSH
```bash
# é necessário navegar ao diretório onde os arquivos da chave foram criados para acessar seu conteúdo
$ cd C:\<current dir>/ .ssh

# ou utilizar o comando $ explorer.exe . para abrir o diretório atual e ter acesso as pastas
```

## contexto windows - CMD
```bash
# listar os arquivos do diretório
$ C:\current_dir>dir
$ id_rsa.
$ id_rsa.pub.

# acessar conteúdo do documento .pub para copiar a chave SSH
$ C:\current_dir>type id_rsa.pub.
```

## contexto WSL / Linux - Bash
```bash
# listar os arquivos do diretório
$ C:\current_dir>ls
$ id_rsa.
$ id_rsa.pub.

# acessar conteúdo do documento .pub para copiar a chave SSH
$ C:\current_dir>cat id_rsa.pub.
```
