
# Exercícios: Processos e serviços Linux

## Vamos colocar a mão na massa DE NOVO!

Agora que conhecemos os principais comandos para administrar processos e serviços, chegou a hora de testar.

Não tenha pressa! Execute cada comando, observe o resultado e tente entender o que está acontecendo. 

A ideia não é simplesmente copiar comandos, mas aprender a interpretar as informações que o Linux apresenta. Se não entendeu, tenta de novo.

---

## Exercício 1 — Conhecendo os processos

Vamos identificar os processos em execução.

1. Liste os processos do seu terminal:

```bash
ps
```

2. Liste todos os processos do sistema:

```bash
ps aux
```

3. Visualize os processos em formato de árvore:

```bash
pstree
```

**Desafio:**
- Quantos processos aparecem na listagem?
- O que significa a coluna PID?
- Qual a diferença entre `ps` e `ps aux`?

Anote. Lembre o cenário.

---

## Exercício 2 — Encontrando processos

Localize processos específicos.

1. Execute:

```bash
ps aux | grep bash
```

2. Agora execute:

```bash
pgrep bash
```

3. Compare os resultados.

**Desafio:**

Explique com suas palavras a diferença entre `grep` e `pgrep` nesse contexto acima.

---

## Exercício 3 — Monitoramento em tempo real

Acompenhe o consumo de recursos.

1. Execute:

```bash
top
```

2. Observe as informações de CPU e memória.
3. Identifique alguns processos que estão em execução.
4. Pressione `q` para sair.

Se tiver o htop instalado, execute também:

```bash
htop
```

**Desafio:**

- Qual processo está consumindo mais CPU?
- Qual está utilizando mais memória?
- Qual a diferença visual entre `top` e `htop`?

---

## Exercício 4 — Criando e finalizando um processo

Entenda como um processo é iniciado e encerrado.

1. Execute:

```bash
sleep 300 &
```

O comando inicia um processo que ficará aguardando por 300 segundos em segundo plano.

2. Localize o processo:

```bash
pgrep -af sleep
```

3. Identifique o PID.
4. Finalize o processo:

```bash
kill PID
```

Substitua PID pelo número identificado.

5. Confira se ele foi encerrado:

```bash
pgrep -af sleep
```

**Desafio:**

O que aconteceu com o processo depois do comando `kill`?

---

## Exercício 5 — Conhecendo os serviços

Consultando o funcionamento dos serviços Linux.

1. Consulte o status do serviço SSH:

```bash
systemctl status ssh
```

2. Liste os serviços em execução:

```bash
systemctl list-units --type=service --state=running
```

3. Verifique se o SSH está habilitado para iniciar automaticamente:

```bash
systemctl is-enabled ssh
```

**Desafio:**

- O serviço SSH está ativo?
- Ele está habilitado para iniciar junto com o sistema?
- Qual a diferença entre um serviço ativo e um serviço habilitado?

Observação: se o SSH não estiver instalado, não precisa instalá-lo apenas para este exercício. Podemos trabalhar com outro serviço disponível no ambiente.

---

## Exercício 6 — Consultando logs

Investigue os registros de um serviço.

1. Consulte os logs do SSH:

```bash
journalctl -u ssh -n 20
```

2. Consulte os últimos registros do sistema:

```bash
journalctl -n 30
```

3. Observe as datas, horários e mensagens.

**Desafio:**

- O que são logs?
- Por que eles são importantes?
- Como os logs podem ajudar a identificar um problema em um servidor?

---

## Exercício 7 — Simulando uma investigação

Aplicando todo o conhecimento em uma situação próxima da realidade.

Imagine o seguinte cenário:

Você recebeu uma solicitação: uma aplicação hospedada em um servidor Linux parou de responder.

Seu primeiro desafio é investigar antes de tentar resolver.

Responda:

1. Qual comando você utilizaria para procurar o processo da aplicação?
2. Como verificaria o consumo de CPU e memória?
3. Como consultaria o status do serviço?
4. Qual comando utilizaria para consultar os logs?
5. O que você analisaria antes de reiniciar o serviço?

Não existe investigação sem que você pare para olhar e entender as evidências.

---

## Desafio final — Seu primeiro diagnóstico Linux

Imagine que você está trabalhando como administrador de infraestrutura. Um serviço apresenta falhas intermitentes e você precisa descobrir o que está acontecendo.

Monte uma pequena sequência de comandos para:

- Identificar os processos.
- Verificar o consumo de recursos.
- Consultar o serviço.
- Analisar os logs.
- Registrar sua conclusão.

Documente os comandos utilizados e explique o que descobriu com eles.

