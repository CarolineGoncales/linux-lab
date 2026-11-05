
# Módulo 03 — Processos e serviços Linux

## Aprendendo a enxergar o que acontece por trás do sistema!

Até aqui, vimos como navegar pelo Linux, trabalhar com arquivos, usuários e permissões.

Agora vamos dar mais um passo: entender o que está acontecendo enquanto o sistema está funcionando.

Você já parou para pensar em quantos processos estão sendo executados no seu computador neste exato momento? Vários!

Um servidor Linux pode executar dezenas ou até centenas de processos simultaneamente. Alguns são iniciados pelo próprio sistema, outros por aplicações e serviços.

Nosso objetivo é aprender a identificar, monitorar e administrar esses processos.

## 1. O que são processos?

Um processo é um programa em execução.

Quando executamos um comando, abrimos um terminal ou iniciamos uma aplicação, podemos aqui, criar um processo. E cada processo possui um identificador chamado PID (Process ID).

Para visualizar os processos em execução:

```bash
ps
```

Para visualizar todos os processos do sistema:

```bash
ps aux
```

Para visualizar os processos em formato de árvore:

```bash
pstree
```

Caso o comando não esteja instalado no Ubuntu:

```bash
sudo apt install psmisc
```

Acostume-se em encontrar SUDO em comandos, ok? De forma simples, ele é o que executa um comando com poderes de administrador e volta ao normal logo em seguida. Então, sudo é assumir permissões premium naquele momento.


## 2. Identificando processos

Alguns comandos ajudam a localizar processos específicos.

Pesquisar um processo pelo nome:

```bash
ps aux | grep nginx
```

Visualizar o PID de um processo:

```bash
pgrep nginx
```

Visualizar informações detalhadas de um processo:

```bash
ps -p PID -f
```

Substitua PID pelo identificador real do processo, confirme vimos no comando anterior.

## 3. Monitoramento em tempo real

O Linux oferece ferramentas para acompanhar o funcionamento do sistema.

### Comando top

```bash
top
```

Permite acompanhar processos, consumo de CPU, memória e outras informações.

Para sair, pressione:

```text
q
```

### Comando htop

```bash
htop
```

Oferece uma visualização mais amigável dos processos.

Se não estiver instalado:

```bash
sudo apt install htop
```

## 4. Finalizando processos

Em algumas situações, um processo pode parar de responder ou consumir recursos excessivos. 

Para finalizar um processo pelo PID:

```bash
kill PID
```

Para solicitar a finalização imediata:

```bash
kill -9 PID
```

Também podemos finalizar pelo nome:

```bash
pkill nome_do_processo
```

ATENÇÃO: antes de finalizar qualquer processo, identifique o que ele faz! Encerrar processos importantes pode causar falhas no sistema ou interromper aplicações. E isso é sério!

## 5. O que são serviços Linux?

Serviços são programas que executam tarefas em segundo plano.

Alguns exemplos:

- SSH: permite acesso remoto ao servidor.
- Nginx: servidor web.
- Cron: executa tarefas agendadas.
- PostgreSQL: banco de dados.

No Ubuntu, podemos administrar muitos desses serviços usando o systemctl.

## 6. Administrando serviços com systemctl

Verificar o status de um serviço:

```bash
systemctl status ssh
```

Iniciar um serviço:

```bash
sudo systemctl start ssh
```

Parar um serviço:

```bash
sudo systemctl stop ssh
```

Reiniciar um serviço:

```bash
sudo systemctl restart ssh
```

Recarregar configurações sem reiniciar completamente o serviço:

```bash
sudo systemctl reload nginx
```

Habilitar um serviço para iniciar junto com o sistema:

```bash
sudo systemctl enable ssh
```

Desabilitar a inicialização automática:

```bash
sudo systemctl disable ssh
```

Verificar os serviços ativos:

```bash
systemctl list-units --type=service --state=running
```

## 7. Consultando logs com journalctl

Logs são registros de acontecimentos do sistema e dos serviços. Eles são fundamentais para investigar problemas.

Deu erro alí? Olhe os logs.

Visualizar os logs do sistema:

```bash
journalctl
```

Visualizar os logs de um serviço:

```bash
journalctl -u ssh
```

Visualizar os últimos registros:

```bash
journalctl -n 50
```

Acompanhar os logs em tempo real:

```bash
journalctl -f
```

Consultar os logs desde a inicialização atual:

```bash
journalctl -b
```

Para sair da visualização, pressione `q` ou `Ctrl + C` (conforme o comando utilizado).

## 8. Por que isso é importante?

Imagine que uma aplicação parou de responder em um servidor. Por onde começaríamos?

1. Verificar se o processo está em execução.
2. Analisar o consumo de CPU e memória.
3. Verificar o status do serviço.
4. Consultar os logs.
5. Identificar a causa do problema.
6. Aplicar a correção necessária.

É assim que começamos a desenvolver uma visão de administração de infraestrutura e troubleshooting. Nome chique, né? É mais difícil pronunciar sem travar, do que entender o que ele é.

