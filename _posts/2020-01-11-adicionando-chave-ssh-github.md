---
layout: post
title: "Adicionando chave SSH ao GitHub"
author: rafael
categories: [github, ssh, tutorial]
image: assets/images/2020/01/11/01.png
featured: true
hidden: true
---

Pode ser muito fácil seguir a [documentação oficial do GitHub](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account) sobre como adicionar sua chave SSH à sua conta. Porém aqui você vai encontrar uma forma muito mais rápida de adicionar sua chave SSH ao GitHub caso você use alguma distribuição Linux.

# Gerando uma chave SSH

## Verifique a existência de uma chave:

```shell=
ls -al ~/.ssh
```

O nome do seu arquivo de chaves públicas pode ser algum da lista abaixo:

- id_dsa.pub
- id_ecdsa.pub
- id_ed25519.pub
- id_rsa.pub

## Gere uma nova chave SSH se necessário

```shell=
ssh-keygen -t rsa -b 4096 -C "seu_email@exemplo.com"
```

Essa mensagem será exibida no terminal:

```shell=
> Enter a file in which to save the key (/home/you/.ssh/id_rsa): [Press enter]
```

A mensagem solicita um local e um nome para o seu arquivo de chave pública. Nesse caso, basta apenas pressionar a tecla [enter] para usar o local e o nome padrão ou então informar uma de sua preferência.

Em seguida, será solicitada a criação de uma senha, porém não é obrigatória. Caso prefira usar a segurança, não esqueça de anotar a senha em um local seguro, como um gerenciador de senhas.

## Adicionando uma chave SSH ao GitHub

Para exibir sua chave SSH pública, execute o comando `ls -al ~/ssh`, identifique o nome do arquivo e então mostre o conteúdo do arquivo no console com o comando:

```shell=
cat ~/.ssh/id_rsa.pub
```

Então:
- Copie a chave que é exibida no seu console após a execução do comando acima
- Vá para a [página de configuração de chaves SSH e GPG do GitHub](https://github.com/settings/keys)
- Clique em [New SSH Key](https://github.com/settings/ssh/new)
- Preencha o campo `Title`. Escolha um nome para identificar o computador, como `Notebook Ubuntu Empresa`
- Cole a sua chave SSH no campo`Key`, pressionando o botão `Add SSH key` em seguida.

A partir de agora, todas as interações entre o seu computador e o GitHub, como `clone`, `push`, `pull` e outros, podem ser realizados com segurança, sem a necessidade de informar seu nome de usuário e senha todas as vezes que executar um novo comando.