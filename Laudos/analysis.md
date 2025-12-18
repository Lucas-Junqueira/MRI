# Índice

Notebooks:
- analiseDadosFaltantes.ipynb
- caracterizacaoLaudos.ipynb
- classificacaoFazekas_Camila.ipynb
- classificacaoFazekas.ipynb
- metadadosDicom.ipynb

CSVs:
- Exames faltantes (lotes 1, 2, 4, 5-1, 6)
  - Código de todos os pacientes com exames faltantes de cada lote
- Exames (lotes 1, 2, 3-1, 3, 4-1, 4, 5-1, 5, 6-1, 6)
  - Código e caminho de todos os exames de cada lote
- Laudos faltantes (lotes 1, 2, 4, 5-1, 6)
  - Código e caminho de todos os laudos faltantes de cada lote
- Laudos (lotes 1, 2, 4, 5-1, 6)
  - Dados extraídos dos laudos, contém: código, indicação, técnica, aspectos e impressão
- laudosi.csv (?)
- laudos_classificados_fazekas.csv
  - dados extraídos dos exames que foram classificados na escala fazekas, contém: caminho, código, indicação, técnica, aspectos, impressão e fazekas

TXTs:
- falha_leitura_dicom.txt
  - Caminho dos exames que tiveram falha no script de leitura

# Análise dos Notebooks

## analiseDadosFaltantes.ipynb

Para cada lote, esse notebook lê a lista de laudos e a lista de exames, e por fim compara as duas, descobrindo quais exames tem imagens faltantes, e quais tem laudos faltantes, utilizando o código e o caminho das pastas. Esse Notebook é reponsável pela criação dos CSVs exames_faltantes_LOTE{i}.csv e dos laudos_faltantes_LOTE{i}.csv

obs: o código (no arquivo de laudos) corresponde ao acession number (no arquivo de exames).

## caracterizacaoLaudos.ipynb

Esse notebook transforma os laudos .RTF em formato CSV, e com base neles faz uma análise exploratória das informações obtidas. Além disso, o notebook é responsável pela criação dos CSVs LOTE{i}_laudos.csv.

### Conversão e Estruturação dos Dados
Os laudos são convertidos de RTF para texto puro e organizados em CSV,
com as seguintes seções:
- Indicação Clínica
- Aspectos Técnicos
- Aspectos Observados
- Impressão

### Processamento de Texto
O texto é normalizado por:
- remoção de acentos
- conversão para minúsculas
- remoção de stopwords
- tokenização em português

### Estatísticas Descritivas
São calculadas:
- contagens de palavras por seção
- total de palavras por laudo
- estatísticas agregadas por lote


### Frequência e Visualização
A análise de frequência identifica os termos mais recorrentes:
- por seção
- no conjunto total de laudos

Os resultados são apresentados por:
- tabelas
- gráficos de barras
- nuvens de palavras

### TF-IDF
O TF-IDF é utilizado para destacar palavras com maior relevância semântica
em cada seção do laudo, reduzindo o impacto de termos muito comuns.

### N-gramas
São analisados:
- bigramas
- trigramas

Essa abordagem permite identificar expressões recorrentes e padrões linguísticos mais complexos, tanto por seção quanto no texto completo.

## classificacaoFazekas_Camila.ipynb

Esse notebook utiliza principalmente os campos "aspectos" e "impressão" para identificar a escala fazekas nos laudos através de técnicas de NLP.

### Contexto e Limitações
A classificação de Fazekas aparece nos laudos de formas variadas, incluindo:
- diferentes convenções textuais
- uso de números romanos ou descrições qualitativas
- menções em diferentes seções do laudo

Além disso, existem casos ambíguos (ex: múltiplos graus no mesmo texto) e possibilidade de menções em seções que não fazem parte da base analisada.

### Estratégia de Processamento
1. Normalização textual por substituição de sinônimos
2. Padronização de graus qualitativos para valores numéricos
3. Extração via expressões regulares
4. Prioridade de busca:
   - Impressão
   - Aspectos

### Identificação da escala Fazekas
A escala é identificada quando ocorre uma expressão clara do tipo:
- `fazekas 1`
- `fazekas grau 2`

Casos ambíguos como `fazekas 2/3` são tratados separadamente.

### Resultados Quantitativos
São calculadas:
- quantidade absoluta de laudos com classe identificada
- porcentagem de cobertura em relação ao total
- quantidade de laudos que mencionam Fazekas independentemente da extração

Essas métricas permitem avaliar a eficácia do método.

### Casos Ambíguos
Laudos contendo múltiplos graus de Fazekas são exportados para um arquivo específico (`laudos_varios_graus.csv`) para análise manual ou refinamento futuro do método.

### Conclusão
O notebook implementa uma abordagem baseada em regras para extração da
classificação de Fazekas, adequada como etapa inicial de caracterização.
Os resultados destacam tanto o potencial quanto as limitações do método,
servindo de base para evoluções futuras com NLP mais avançado.

## classificacaoFazekas.ipynb

Este notebook implementa um método baseado em regras para identificar automaticamente a classe de Fazekas em laudos médicos estruturados em CSV, representando um refinamento do procedimento exploratório adotado anteriormente.

### Desafio
A escala de Fazekas aparece nos laudos com grande variabilidade textual, incluindo:
- diferentes ordens sintáticas
- uso de algarismos romanos e arábicos
- variações linguísticas e descrições intermediárias
- casos ambíguos com múltiplos graus

Além disso, a informação pode estar presente em mais de uma seção do laudo, principalmente **Aspectos** e **Impressão**, o que exige uma estratégia de busca consistente.

### Metodologia
1. Leitura e consolidação de múltiplos lotes de laudos em um único DataFrame.
2. Extração da classe de Fazekas com prioridade na seção **Impressão** e fallback em **Aspectos**.
3. Aplicação de expressões regulares flexíveis, capazes de capturar variações reais de escrita, incluindo palavras intermediárias, inversão de ordem e algarismos romanos.
4. Padronização da classe extraída para uma representação numérica única.
5. Identificação de casos ambíguos com mais de um grau e consolidação por média aritmética.
6. Verificações adicionais para validar falhas residuais e confirmar a consistência dos resultados.

Em relação ao notebook anterior, essa metodologia amplia a tolerância a variações textuais e reduz a necessidade de inspeção manual.

### Casos Ambíguos
Laudos que apresentam mais de um grau de Fazekas (ex.: `1/2`, `ii/iii`) são tratados separadamente e transformados em um valor médio, preservando a
informação semântica do texto e permitindo sua incorporação em análises quantitativas.

### Resultados
O método alcança alta cobertura na identificação da escala de Fazekas, com redução de perdas associadas a variações linguísticas e ambiguidades quando comparado à abordagem anterior.

A coluna final **Fazekas** consolida todos os casos detectados e está pronta para uso em análises clínicas, estatísticas ou modelos de aprendizado de máquina.

## metadadosDicom.ipynb

Este notebook tem como objetivo gerar uma base estruturada contendo os exames disponíveis em formato DICOM, associando o **Accession Number**
ao **caminho do arquivo**, a partir da varredura do diretório de imagens de um lote.

### Objetivo
Identificar e catalogar exames presentes nos diretórios de imagens DICOM, criando um arquivo CSV que permita a correspondência entre:
- identificador do exame (`Accession Number`)
- localização física do arquivo no sistema de arquivos

Essa base é utilizada posteriormente para cruzamento com os laudos.

### Metodologia
1. Leitura de um arquivo DICOM de exemplo para validação do acesso aos metadados.
2. Varredura recursiva dos diretórios do lote de imagens utilizando `os.walk`.
3. Leitura de cada arquivo DICOM com a biblioteca `pydicom`.
4. Extração do campo **Accession Number** diretamente do cabeçalho DICOM.
5. Armazenamento do primeiro caminho válido associado a cada exame.
6. Consolidação dos resultados em um DataFrame com as colunas:
   - `Accession Number`
   - `Path`
7. Exportação do resultado para um arquivo CSV no formato `exames_<LOTE>.csv`.

Em relação a versões anteriores do processo, este notebook automatiza a extração diretamente dos metadados DICOM, eliminando a necessidade de
listas manuais ou correspondências externas.

### Tratamento de Erros
Arquivos que não correspondem a DICOM válidos são ignorados por meio de tratamento de exceção (`InvalidDicomError`), garantindo a continuidade da
execução sem interrupções.

### Resultado
O notebook gera um arquivo CSV contendo todos os exames identificados no
lote, com seus respectivos caminhos, possibilitando:
- cruzamento com bases de laudos
- identificação de exames sem laudo
- rastreabilidade dos arquivos originais