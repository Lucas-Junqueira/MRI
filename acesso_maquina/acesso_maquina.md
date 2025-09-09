O dataset inteiro está contido na máquina 'gorgona1' do Speed, que fica em uma sala fechada do CRC. O acesso a máquina é restrito, pois os dados são sensíveis e também são propriedade do grupo Fleury, também é por isso que a gorgona1 fica separada das outras.

Para acessarmos a máquina, usaremos o protocolo SSH (Secure Shell) para criar uma conexão remota com a gorgona1. Se você não sabe o que é SSH ou nunca o utilizou, não se preocupe, vamos ensinar o passo a passo de como utilizá-lo.

# O que é SSH e Como Utilizá-lo

O SSH (Secure Shell) é um protocolo de rede que permite acessar e administrar computadores remotamente de forma segura. Ele permite que possamos interagir com um computador remoto por terminal.

Para realizar uma conexão SSH, será necessário utilizar um nome de usuário e o endereço da máquina/servidor remoto que você deseja acessar. O comando deve ser dado por um terminal e a sintaxe do comando SSH é a seguinte:

```
ssh usuario@servidor.com
```

Se for sua primeira vez se conectando a uma máquina/servidor específico, o SSH pergunta se você confia na chave do servidor (você responde com 'yes' para continuar com acesso). Depois, você entra com sua senha.

# O acesso a Gorgona1

## Pré-Requisitos

Antes de realizarmos o acesso, saiba que existem três pré-requisitos para acessar a máquina:

1. Você deve pedir ao seu professor orientador (possivelmente o Meira) para enviar um pedido ao CRC para vincular seu usuário DCC ao grupo Speed.
2. Você deve pedir ao administrador do Speed para criar uma conta de usuário para você dentro do grupo speed. Esse pedido pode ser feito no seguinte [Grupo Do Telegram]().
3. Você deve pedir ao administrador da gorgona1 para liberar o seu acesso na máquina.

## O acesso com SSH

Agora que você já sabe como utilizar o SSH e já tem os requisitos de acesso, vamos ver como se acessa a máquina que contém os dados. Para isso, precisaremos realizar dois SSHs consecutivos.

O primeiro SSH deve ser feito para que você gere uma conexão com a máquina geral do CRC (antiga mica), o endereço dela é *login.dcc.ufmg.br** e você deve acessá-la com seu usuário CRC, ou seja, o comando deve ser o seguinte:

```
ssh usuario_crc@login.dcc.ufmg.br
```

Você também deve utilizar a sua senha do CRC (a mesma que você utiliza para acessar seu email DCC) para fazer o login na maquina. Depois, de acessar a máquina, você vera algo como isso em seu terminal:

IMAGEM AQUI!!!

# O acesso a Gorgona1 com Vscode 