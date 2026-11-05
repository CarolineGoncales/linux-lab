# Comandos básicos do Linux

## Vamos começar pelo começo?

Antes de sair executando comandos, quero te fazer uma pergunta: você sabe realmente o que está acontecendo quando abre um terminal?

O terminal é uma das ferramentas mais importantes para quem trabalha com Linux. É por meio dele que conseguimos conversar diretamente com o sistema operacional, executar tarefas, administrar recursos e investigar problemas. Não, não é só uma tela preta sem sentido.

E não se assuste com a tela cheia de letras! Parece complicado no começo, mas, quando você entende a lógica, quase tudo começa a fazer sentido.

Minha proposta aqui é simples: vamos aprender um comando de cada vez, testar e entender o resultado.

Se você veio de algum curso que gravei, já deve saber que eu gosto de repetir muitas vezes coisas básicas para que fixe de verdade (eu sei, fica até chato). Mas, sem o básico, nós não saímos do lugar.

## 1. Primeiro, onde estamos?

Imagine que você entrou em uma casa, mas não sabe em qual cômodo está. Antes de procurar alguma coisa, precisa descobrir, certo?

No Linux, usamos:

pwd

Esse comando mostra o caminho do diretório em que estamos.

**Agora experimente você!** 

Abra seu terminal, digite `pwd` e observe o resultado.

## 2. O que existe neste lugar?

Agora que sabemos onde estamos, vamos descobrir o que existe nesse diretório. Use:

ls

Esse comando lista os arquivos e as pastas.

Mas quero que você experimente também:

ls -l
ls -la

Percebeu a diferença?

- `ls`: mostra os arquivos e diretórios.
- `ls -l`: apresenta informações detalhadas.
- `ls -la`: também mostra arquivos ocultos.

## 3. Vamos passear pelos diretórios?

Para entrar em uma pasta, utilizamos:

cd nome-da-pasta-aqui


Quer voltar um nível?

cd ..


Quer voltar para seu diretório pessoal?

cd ~

Navegue entre as pastas. Não tenha medo de testar e se perder!

## 4. Criando nossas próprias pastas

Chegou a hora de colocar a mão na massa.

mkdir laboratorio

Pronto! Você acabou de criar um diretório chamado `laboratorio`.

E se quiser criar um arquivo?

touch anotacoes.txt


Simples assim!

## 5. Alguns comandos que você precisa conhecer


| `whoami` | Mostra qual usuário está conectado |

| `uname -a` | Apresenta informações do sistema |

| `df -h` | Mostra o espaço utilizado e disponível em disco |

| `free -h` | Mostra informações sobre a memória |

| `top` | Permite acompanhar os processos em execução |

| `clear` | Limpa a tela do terminal |


## Minha dica até aqui

Não tente decorar tudo de uma vez. Execute os comandos, observe o resultado e procure entender o que aconteceu.
