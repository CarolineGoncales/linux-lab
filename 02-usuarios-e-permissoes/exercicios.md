# Exercícios — Usuários e permissões Linux

## Chega de só olhar! Agora é sua vez!

Até aqui, conhecemos alguns comandos para trabalhar com usuários, grupos e permissões.

Mas você realmente entendeu como tudo isso funciona?

Vamos imaginar uma situação: você foi responsável por organizar os acessos de um servidor Linux e precisa preparar o ambiente para uma pequena equipe. Vamos resolver isso agora.

## Desafio 01 — Quem sou eu no Linux? Ou a pergunta seria 'quem é você no Linux?'

Abra seu terminal e execute:

whoami
id
groups


Agora responda:

1. Qual usuário está conectado?
2. Qual é o seu UID?
3. Quais grupos aparecem para esse usuário?


## Desafio 02 — Investigando os usuários

Execute:

cat /etc/passwd

Observe as informações apresentadas e responda:

1. Onde aparecem os nomes dos usuários?
2. O que significa UID?
3. Todos os usuários listados representam pessoas?

Agora consulte os grupos:

cat /etc/group


Conseguiu perceber como o Linux organiza essas informações?

## Desafio 03 — Criando um novo usuário

Vamos criar um usuário chamado `aluno-lab`.

sudo adduser aluno-lab


Depois, consulte:

id aluno-lab


Responda:

1. O usuário foi criado?
2. Qual UID foi atribuído?
3. Qual é o grupo principal?

## Desafio 04 — Criando e modificando arquivos

Agora vamos criar um arquivo:

touch arquivo-teste.txt

Consulte suas permissões:

ls -l arquivo-teste.txt


Altere para:

chmod 644 arquivo-teste.txt


Consulte novamente:

ls -l arquivo-teste.txt


**Pergunta:** o que mudou?

## Desafio 05 — Decifrando o chmod

Quero ver se você entendeu a lógica dos números!

Sem consultar a explicação, tente descobrir o significado de cada combinação:

| `chmod 600 arquivo.txt` | O que permite? |
| `chmod 700 arquivo.sh` | O que permite? |
| `chmod 755 arquivo.sh` | O que permite? |
| `chmod 644 arquivo.txt` | O que permite? |

Lembre-se: leitura vale 4, escrita vale 2 e execução vale 1.

## Desafio 06 — Organizando uma equipe

Imagine que você está administrando um servidor e precisa criar um grupo chamado `equipe-ti`.

Execute:

sudo groupadd equipe-ti


Agora adicione o usuário `aluno-lab`:

sudo usermod -aG equipe-ti aluno-lab


Confira:

groups aluno-lab


Responda:

1. O grupo foi criado?
2. O usuário foi adicionado?
3. Por que é interessante trabalhar com grupos em um servidor?

## Desafio 07 — Uma situação reeeeal de infraestrutura

Imagine que uma empresa possui um servidor Linux utilizado por três profissionais:

- Administrador: precisa acessar e modificar os arquivos.
- Desenvolvedor: precisa ler e modificar os arquivos da aplicação.
- Analista: precisa apenas consultar os arquivos.

Agora pense:

1. Você daria acesso total para os três?
2. Como organizaria os usuários e grupos?
3. Quais permissões utilizaria?
4. O que poderia acontecer se todos tivessem acesso administrativo?


## Testando você!

Tente realizar estas tarefas sem consultar os exemplos anteriores:

1. Criar um usuário chamado `teste-ti`.
2. Criar um grupo chamado `infraestrutura`.
3. Adicionar o usuário ao grupo.
4. Criar um arquivo chamado `servidor.conf`.
5. Alterar as permissões para `640`.
6. Consultar o proprietário, grupo e permissões do arquivo.

