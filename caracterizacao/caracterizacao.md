# O Dataset e sua Estrutura

No projeto, nos foi disponibilizado 10.000 exames de MRI, sendo eles divididos em 6 Lotes. Todos os lotes possuem as imagens de ressonância magnética e apenas alguns destes Lotes possuem Laudos. Alguns destes Lotes também são subdivididos e a lista destes pode ser vista a seguir:

| Contém laudos | Não contém laudos |
| --- | --- |
| Lote 1 | Lote 3 |
| Lote 2 | Lote 3-1 |
| Lote 4 | Lote 4-1 |
| Lote 5-1 | Lote 5 |
| Lote 6 | Lote 6-1 |

Todos os lotes estão contidos na `górgona1`, sendo os lotes 1, 2, 3, 3-1, 4-1, 5-1 e 6 contidos no HD2 e os lotes 4, 5 e 6-1 no HD1. Além disso, em cada lote, temos a seguinte estrutura:

📂 Lote  
└── 📂 Paciente  
‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ └── 📂 Exame_Série  
‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ └── 📄 Dicoms.dcm

E estes podem ser encontrados nos seguintes `paths` da `gorgona1`:

> /mnt/HD_1/dados/pardini  
> /mnt/HD_2/dados/pardini

# Caracterização dos Dados

No dataset, temos em geral:
- Pacientes/ID:
- Studies/Exames:
- Séries: 
- Dicoms:

Neste tópico, é deixado links para caracterizações de metadados contidos no dataset:

- [Series Description](/caracterizacao/metadados/series_description.md)
- [Idades](/caracterizacao/metadados/idades.md)
- [Pesos](/caracterizacao/metadados/pesos.md)
- [Gênero](/caracterizacao/metadados/genero.md)
- [Altura](/caracterizacao/metadados/altura.md)

---
 
> [Retornar para a página inicial](/README.md)