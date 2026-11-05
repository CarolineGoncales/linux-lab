
# Exercícios: Redes e diagnóstico Linux

## Vamos descobrir quem está do outro lado da rede!

Chegou a hora de investigar! Parte dos curiosos.

---

## Exercício 1 — Conhecendo sua rede

Execute:

```bash
ip link
```

Agora:

```bash
ip addr
```

E também:

```bash
ip -br addr
```

**Desafio:**

- Quantas interfaces de rede aparecem?
- Qual é o endereço IP da sua máquina?
- Você encontrou a interface `lo`?
- Para que ela serve?

---

## Exercício 2 — Descobrindo seu endereço IP

Entenda a diferença entre IP privado e público.

Execute:

```bash
hostname -I
```

Depois:

```bash
curl ifconfig.me
```

**Desafio:**

- Qual é o seu IP privado?
- Qual é o seu IP público?
- Por que esses endereços podem ser diferentes?

Dica importannnteee!: não publique seus endereços IP em ambientes públicos sem necessidade.

---

## Exercício 3 — Tem alguém aí? 😂

Execute:

```bash
ping -c 4 google.com
```

Agora teste diretamente um endereço IP:

```bash
ping -c 4 8.8.8.8
```

**Desafio:**

- Quantos pacotes foram enviados?
- Quantos foram recebidos?
- Houve perda de pacotes?
- Qual foi o tempo médio de resposta?

Agora relembre o que falamos... Iimagine que você pergunta: "Tem alguém aí?"

*MERCADO LIVREEEEEEEEEEEE* 

E o servidor responde: "Tem! Toma aqui suas encomendas!" 

Explique o que representa essa troca de mensagens.

---

## Exercício 4 — Investigando o DNS

Como um domínio é convertido em endereço IP?

Execute:

```bash
nslookup google.com
```

Depois:

```bash
dig google.com
```

**Desafio:**

- Qual endereço IP foi retornado?
- Qual servidor DNS respondeu à consulta?
- Por que precisamos do DNS para acessar sites utilizando nomes de domínio?

---

## Exercício 5 — Conhecendo as portas

Execute:

```bash
sudo ss -tulnp
```

Observe as portas que aparecem.

Lembre-se de algumas portas conhecidas:

| Porta | Serviço |
|---|---|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 5432 | PostgreSQL |
| 3306 | MySQL |

**Desafio:**

- Quais portas estão em escuta?
- Você encontrou alguma das portas da tabela?
- Por que um servidor precisa disponibilizar portas para receber conexões?

---

## Exercício 6 — Conhecendo as rotas

Execute:

```bash
ip route
```

Identifique a rota padrão, geralmente indicada pela palavra `default`.

**Desafio:**

- Qual é o gateway padrão?
- Qual interface está sendo utilizada?
- Qual é a importância do gateway para acessar outras redes?

---

## Exercício 7 — Vamos visitar a CPG Consulting! 😂

Agora vamos aproveitar para fazer uma visita ao nosso próprio laboratório de testes: a CPG Consulting!

Primeiro, consulte o site:

```bash
curl https://cpgconsulting.com.br/
```

Depois, consulte somente os cabeçalhos HTTP:

```bash
curl -I https://cpgconsulting.com.br/
```

Agora, veja os detalhes da comunicação:

```bash
curl -v https://cpgconsulting.com.br/
```

**Desafio:**

- O site respondeu à requisição?
- Qual código HTTP foi retornado?
- O que significa o código `200`?
- Qual é a diferença entre executar `curl`, `curl -I` e `curl -v`?

Dica: se aparecer `200 OK`, temos uma resposta de sucesso para aquela requisição HTTP.

Olha só! Estamos investigando um servidor real usando comandos Linux. 😎 Nada de querer me burlar, hein?

---

## Exercício 8 — Investigação de conectividade

Imagine que um usuário informa: "Estou tentando acessar um site, mas ele não abre!"

Você precisa investigar antes de afirmar onde está o problema.

Utilize os comandos que aprendemos para responder:

1. A interface de rede está ativa?
2. A máquina possui endereço IP?
3. Existe comunicação com um endereço externo?
4. O DNS está resolvendo o domínio?
5. O servidor responde na porta HTTPS?
6. O site retorna uma resposta HTTP?

Registre os resultados e tente identificar onde está a falha.

---

## Desafio final — Você é o responsável pela rede!

Eu gosto de trabalhar a imaginação. Então, imagine que você recebeu um chamado:

"Uma aplicação não consegue se comunicar com o banco de dados hospedado em outro servidor."

Monte uma sequência de investigação utilizando os comandos que vimos. Sua análise deverá identificar:

- Endereço IP de origem e destino.
- Conectividade entre as máquinas.
- Resolução DNS.
- Rota de rede.
- Porta utilizada pelo banco de dados.
- Possíveis problemas de comunicação.

Documente os comandos e explique o que cada resultado representa.

E lembrem-se: até a CPG Consulting virou laboratório hoje! 

### Dica de segurança: estamos realizando consultas públicas para fins de diagnóstico. Nunca compartilhe saídas de terminal que contenham senhas, tokens, cookies ou informações de autenticação.