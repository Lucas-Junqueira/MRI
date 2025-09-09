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
2. Você deve pedir ao administrador do Speed para criar uma conta de usuário para você dentro do grupo speed. Esse pedido pode ser feito no seguinte [Grupo Do Telegram](https://t.me/+NTlKuGvnDtw2MjQx).
3. Você deve pedir ao administrador da gorgona1 para liberar o seu acesso na máquina.

## O acesso com SSH

Agora que você já sabe como utilizar o SSH e já tem os requisitos de acesso, vamos ver como se acessa a máquina que contém os dados. Para isso, precisaremos realizar dois SSHs consecutivos.

O primeiro SSH deve ser feito para que você gere uma conexão com a máquina geral do CRC (antiga mica), o endereço dela é **login.dcc.ufmg.br** e você deve acessá-la com seu usuário CRC, ou seja, o comando deve ser o seguinte:

```
ssh usuario_crc@login.dcc.ufmg.br
```

Você também deve utilizar a sua senha do CRC (a mesma que você utiliza para acessar seu email DCC) para fazer o login na maquina. Depois, de acessar a máquina, você vera algo como isso em seu terminal:

![Acesso a Mica](https://github.com/Lucas-Junqueira/MRI/blob/main/acesso_maquina/imagens/acesso_mica.png)

Após acessar a máquina geral do CRC, acessaremos, a partir dela, a gorgona1 utilizando um outro comando SSH. Para acessar a gorgona, você também utilizará o seu usuário e senha do CRC, juntamente com o endereço **gorgona1.speed.dcc.ufmg.br**, ou seja, o comando será o seguinte:

```
ssh usuario_crc@gorgona1.speed.dcc.ufmg.br
```

## Localização dos Dados

Parabéns, agora você conseguiu acessar a maquina! Agora vamos entender onde estão localizados os dados. A gorgona1 contém dois HDs e um SSD, no SSD está a pasta home dos usuários, já nos HDs (localizados na pasta **/mnt**), estão localizados os dados.

O Dataset está dividivo, por questões de memória, nos dois HDs, o HD2 é reservado apenas para os dados e contém a maior parte deles.

Os datasets estão localizados nos seguintes paths:

```
/mnt/HD_1/dados/pardini
/mnt/HD_2/dados/pardini
```

# O acesso a Gorgona1 com Vscode

Também é possível utilizar o Vscode na máquina remota como se você estivesse na sua máquina local. Para isso, siga os passos abaixo:

1. No Vscode, Baixe a extensão Remote-SSH:

![Remote SSH](https://github.com/Lucas-Junqueira/MRI/blob/main/acesso_maquina/imagens/remote_ssh.png)

2. Acesse o arquivo de configuração ('config') do ssh. Ele pode ser acessado da seguinte forma:

![Explorador Remoto](https://github.com/Lucas-Junqueira/MRI/blob/main/acesso_maquina/imagens/explorador_remoto.png)

![Selecionar Arquivo](https://github.com/Lucas-Junqueira/MRI/blob/main/acesso_maquina/imagens/selecionar_arquivo.png)

3. Por fim, edite o arquivo de configuração da seguinte forma:

![Arquivo de Config](https://github.com/Lucas-Junqueira/MRI/blob/main/acesso_maquina/imagens/acesso_mica.png)