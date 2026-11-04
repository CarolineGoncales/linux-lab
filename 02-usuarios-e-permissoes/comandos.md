# Usuários e permissões

## Afinal, quem pode fazer o quê?

Imagine que você está trabalhando na administração de um servidor. Existem várias pessoas utilizando esse ambiente, cada uma com suas responsabilidades.

Será que todas precisam ter acesso a tudo? Claro que não!

É justamente por isso que precisamos entender usuários, grupos e permissões no Linux.

Bora ver como isso funciona?

## 1. Descobrindo quem está conectado

Primeiro, vamos descobrir qual usuário está utilizando o sistema. Nós vimos um comando sobre isso anteriormente, lembra?

whoami

Agora vamos um pouco além:

id

Esse comando apresenta informações sobre o usuário, como UID, GID e grupos.

Mas o que são essas siglas?

- UID é a identificação numérica do usuário.
- GID é a identificação numérica do grupo.
- Grupos é onde permite organizar usuários e controlar acessos.

## 2. Conhecendo os usuários do sistema

Você já parou para pensar onde o Linux guarda as informações dos usuários?

Vamos consultar:

cat /etc/passwd


Agora você vai pensar que é uma tela preta cheia de coisas sem sentido, mas não é. Cada linha representa uma conta cadastrada no sistema. E atenção aqui: nem todas são pessoas! Muitas contas são utilizadas pelos próprios serviços do Linux.

Para conhecer os grupos:

cat /etc/group


## 3. Criando um usuário

Agora vamos colocar a mão na massa!


sudo adduser aluno-lab


O sistema solicitará algumas informações e uma senha.

Mas por que usamos `sudo`?

Porque estamos executando uma operação que exige privilégios administrativos.

Lembre-se: o `sudo` não é um comando para sair utilizando sem pensar. Antes de executar qualquer operação administrativa, entenda o que ela faz.

## 4. Entendendo as permissões

Aqui está uma das partes mais importantes!

No Linux, trabalhamos com três permissões básicas:

| Permissão | Significado | Valor |
|---|---|---|
| r | Leitura | 4 |
| w | Escrita | 2 |
| x | Execução | 1 |

E essas permissões são aplicadas a três categorias:

- Usuário: proprietário do arquivo.
- Grupo: grupo associado ao arquivo.
- Outros: demais usuários do sistema.

Vamos visualizar?

ls -l

Um resultado pode ser parecido com este:

```text
-rwxr-xr-- 1 usuario grupo 1200 arquivo.sh
```

Traduzindo:

- Proprietário: pode ler, escrever e executar.
- Grupo: pode ler e executar.
- Outros: podem apenas ler.

Percebeu como podemos controlar o acesso aos arquivos?

## 5. Modificando permissões com chmod

Vamos criar um arquivo para testar:


touch teste.txt


Agora vamos alterar suas permissões:


chmod 644 teste.txt


Mas de onde veio esse número?

- 6 = leitura (4) + escrita (2).
- 4 = leitura.
- 4 = leitura.

Outro exemplo:


chmod 755 script.sh


Nesse caso, o proprietário pode ler, escrever e executar. O grupo e os demais usuários podem ler e executar.

## 6. Alterando o proprietário com chown

Imagine que um arquivo pertence ao usuário errado. Como podemos mudar isso?

Utilizamos:


sudo chown aluno-lab teste.txt


Também podemos alterar o proprietário e o grupo:


sudo chown aluno-lab:aluno-lab teste.txt


Para conferir:


ls -l teste.txt


## 7. Criando grupos

Quando várias pessoas precisam acessar determinados arquivos, trabalhar com grupos facilita bastante.

Para criar um grupo:


sudo groupadd equipe-lab


Para adicionar um usuário:


sudo usermod -aG equipe-lab aluno-lab


E para conferir:

groups aluno-lab


A opção `-aG` adiciona o grupo sem substituir os outros grupos complementares do usuário.

## 8. Mas, e na vida real, onde utilizamos tudo isso?

Imagine um servidor de produção com uma equipe trabalhando.

Uma pessoa precisa consultar logs, outra precisa executar uma aplicação e somente o administrador deve alterar determinadas configurações.

Se todos tiverem acesso irrestrito, podemos criar um grande problema de segurança. Grande mesmo!

Por isso, administrar permissões é muito mais do que conhecer comandos: é entender responsabilidades e proteger o ambiente.
