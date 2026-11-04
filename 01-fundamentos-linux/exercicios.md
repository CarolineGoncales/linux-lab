# Exercícios — Linux

## Agora é com você!

Aqui temos alguns desafios para praticarmos os comandos que acabamos de conhecer. Pode parecer simples, mas nós começamos pelo básico mesmo.

Não se preocupe se errar. O objetivo não é acertar tudo de primeira, mas entender o que está fazendo.

### Desafio 01 — Descobrindo onde estou

1. Abra o terminal.
2. Execute `pwd`.
3. Identifique o diretório em que você está.

**Pergunta:** o que esse comando informa?

### Desafio 02 — Explorando arquivos

1. Execute `ls`.
2. Depois execute `ls -la`.
3. Compare os resultados.

**Pergunta:** quais arquivos apareceram somente na segunda execução?

### Desafio 03 — Criando seu primeiro laboratório

Execute:

```bash
mkdir meu-primeiro-lab
cd meu-primeiro-lab
touch minhas-anotacoes.txt
ls -la
```

**Desafio:** explique o que aconteceu em cada etapa. Anote!

### Desafio 04 — Conhecendo o sistema

Execute:

whoami
uname -a
df -h
free -h

Agora responda:

- Qual usuário está conectado?
- Qual sistema operacional ou kernel está utilizando?
- Quanto espaço existe disponível em disco?
- Quanto de memória está disponível?

### Desafio 05 — Testando sua memória

Sem consultar, tente:

1. Criar uma pasta chamada `desafio-linux`.
2. Entrar nela.
3. Criar um arquivo chamado `teste.txt`.
4. Listar o conteúdo da pasta.
5. Voltar para o diretório anterior.

