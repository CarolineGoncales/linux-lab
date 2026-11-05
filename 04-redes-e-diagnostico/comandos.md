
# Módulo 04 — Redes e diagnóstico Linux

## Entendendo como as máquinas se comunicam!

Até aqui, vimos como trabalhar com arquivos, usuários, permissões, processos e serviços. Agora vamos entender como o Linux se comunica com outras máquinas.

Imagine um servidor que está funcionando perfeitamente, mas não consegue acessar a internet. Ou uma aplicação que está no ar, mas não consegue se comunicar com o banco de dados. Por onde começaríamos a investigar?


## 1. Identificando as interfaces de rede

Uma interface de rede é o componente responsável pela comunicação do computador com uma rede. Confesso que esse tópico sempre gerou uma pequena confusão na minha mente.

Para visualizar as interfaces disponíveis:

```bash
ip link
```

Para visualizar os endereços IP:

```bash
ip addr
```

Ou, de forma resumida:

```bash
ip -br addr
```

Para visualizar as rotas configuradas:

```bash
ip route
```

**Dica:** observe a interface `lo`. Ela representa o endereço de loopback, que é utilizado para comunicação do próprio computador consigo mesmo. Ele com ele, sabe?

## 2. Descobrindo o endereço IP

O endereço IP identifica uma máquina dentro de uma rede.

Para descobrir seu endereço IP público, podemos consultar:

```bash
curl ifconfig.me
```

Para visualizar os endereços configurados nas interfaces locais:

```bash
hostname -I
```

Atenção: o IP público e o IP privado são coisas diferentes. O endereço público identifica sua conexão na internet, enquanto o privado é utilizado dentro de uma rede local. Parece uma observacão de pouca importância, mas é sempre bom lembrar.

## 3. Testando a conectividade com ping

O comando `ping` verifica se existe comunicação com outro endereço IP ou domínio. É basicamente um "tem alguém aí?".
Quando executamos um `ping`, nosso computador envia pequenos pacotes de dados ao destino e aguarda uma resposta, tipo um "Tem. Toma aqui suas encomendas."


Exemplo:

```bash
ping google.com
```

Para limitar a quantidade de testes:

```bash
ping -c 4 google.com
```

Também podemos testar diretamente um endereço IP:

```bash
ping -c 4 8.8.8.8
```

**O que observar?**

- Tempo de resposta.
- Pacotes enviados.
- Pacotes recebidos.
- Perda de pacotes.

Importante: alguns servidores bloqueiam respostas ao ping. Portanto, ausência de resposta não significa necessariamente que o servidor está fora do ar.

## 4. Entendendo o DNS

DNS significa Domain Name System. Ele é responsável por traduzir nomes de domínio em endereços IP.

Por exemplo, quando acessamos um site pelo nome, o DNS ajuda a descobrir para qual endereço IP devemos direcionar a conexão.

Para consultar um domínio:

```bash
nslookup google.com
```

Outra opção:

```bash
dig google.com
```

Se o comando `dig` não estiver disponível:

```bash
sudo apt install dnsutils
```

Para consultar os servidores DNS configurados:

```bash
resolvectl status
```

**Dica importante:** quando um domínio não abre, mas o acesso direto ao IP funciona, vale investigar o DNS.

## 5. Verificando portas de rede

Uma porta identifica um ponto de comunicação utilizado por uma aplicação ou serviço.

Algumas portas conhecidas:

| Porta | Serviço |
|---|---|
| 22 | SSH |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 5432 | PostgreSQL |
| 3306 | MySQL |

Para visualizar as portas em escuta:

```bash
sudo ss -tulnp
```

Para verificar se uma porta específica está acessível em outro servidor:

```bash
nc -vz exemplo.com 443
```

Substitua `exemplo.com` pelo domínio ou IP que você quer.

Se o comando `nc` não estiver instalado:

```bash
sudo apt install netcat-openbsd
```

## 6. Analisando rotas de rede

O Linux utiliza rotas para decidir por onde os pacotes devem seguir até chegar ao destino. 

Para visualizar a tabela de rotas:

```bash
ip route
```

Para identificar o caminho percorrido até um destino:

```bash
traceroute google.com
```

Caso não esteja instalado:

```bash
sudo apt install traceroute
```

Outra alternativa é:

```bash
tracepath google.com
```

Esses comandos ajudam a investigar em qual ponto do caminho podem existir dificuldades de comunicação.

## 7. Testando uma aplicação com curl

O comando `curl` permite fazer requisições para servidores e APIs.

Vou aproveitar esse momento para fazer uma pequena propaganda do meu site! 😂 Afinal, nada melhor do que aprender testando algo real.

**Para consultar um site:**

```bash
curl https://cpgconsulting.com.br/
```

**Para visualizar somente os cabeçalhos HTTP:**

```bash
curl -I https://cpgconsulting.com.br/
```

**Para acompanhar os detalhes da conexão:**

```bash
curl -v https://cpgconsulting.com.br/
```

Agora temos três formas diferentes de conversar com um servidor.

- `curl`: faz a requisição e apresenta a resposta.
- `curl -I`: consulta os cabeçalhos HTTP.
- `curl -v`: mostra detalhes da comunicação.

Isso é muito útil quando precisamos investigar problemas de comunicação entre aplicações.


## 8. Verificando o nome da máquina

O hostname é o nome atribuído ao computador ou servidor.

Para consultar:

```bash
hostname
```

Para visualizar informações mais completas:

```bash
hostnamectl
```

Para alterar o nome da máquina:

```bash
sudo hostnamectl set-hostname novo-nome
```

Substitua `novo-nome` pelo nome desejado.

## 9. Como investigar problemas de rede?

Imagine que uma aplicação não consegue acessar um banco de dados remoto.

Podemos começar nossa investigação:

1. Verificar se a interface de rede está ativa.
2. Conferir o endereço IP.
3. Consultar a tabela de rotas.
4. Testar a conectividade com o destino.
5. Verificar a resolução DNS.
6. Testar se a porta do serviço está acessível.
7. Analisar a resposta da aplicação.

Não precisamos executar todos os comandos aleatoriamente. Cada teste deve ajudar a responder uma pergunta. Se você não sabe qual pergunta tem que responder, veja o cenário novamente, monte os questionamentos e investigue.

