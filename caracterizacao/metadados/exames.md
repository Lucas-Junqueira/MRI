Como mencionado antes, as imagens médicas disponibilizadas pelo Hermes Pardini estão contidas na máquina Gorgona1 da seguinte forma: 
> mnt / HD_# / dados / pardini /LOTE# / IMAGEM / [código ID do paciente] / Study / Serie / .dcm

Ademais, os algoritmos usados para caracterizar o Dataset partiram de uma mesma lógica básica inicial. Para a extração dos metadados próprios dos Dicoms (`Pantient's Sex`, `Patient's Size`, `Patient's Age`, `Patient's Weight`), eram percorridos todos as pastas de pacientes procurando o primeiro Study válido, ou seja, que contivesse pelo menos uma Serie válida, a qual, por sua vez deveria ter um arquivo `.dcm`.

Dessa forma, era solucionado o problema de contar todos os arquivos Dicoms do Dataset para coletar uma informação relativamente constante entre as imagens dos exames, sem contar que o conteúdo de uma série são os diferentes cortes de um mesmo momento (seria possível reconstruir a extrutura 3D do crânio do paciente juntando todas as faixas). Esse método de extração é bem mais rápido, porém desconsidera o envelhecimento/mudança de peso de um paciente entre exames.

Assim, essas são as quantidades de pacientes contabizados ("válidos") na caracterização dos quatro metadados internos aos Dicoms:
>

## Dados brutos: 

Também foram coletados outras estatistísticas que não requeriam algorítmos que se preocupassem com a verificação de diretórios válidos, ou seja, os números a seguir incluem pastas vazias caso elas existam. Assim, foram contabilizados X pacientes, os quais possuem em média 1,20 pastas Study:

![Imagem](/imagens/hist_study.png)

Estas Y pastas Study, por sua vez, apresentam uma média de y1 pastas Serie, ou y2 Serie(s) por paciente:

![Imagem](/imagens/hist_serie.png)

Por fim, o Dataset apresenta Z Dicoms, o que constitui uma média de z1 arquivos de imagem médica por Serie, ou z2 `.dcm` por Study, ou z3 por paciente:

![Imagem](/imagens/hist_dcm.png)

---

> [Retornar para a página anterior](/caracterizacao/caracterizacao.md)  
> [Retornar para a página inicial](/README.md)