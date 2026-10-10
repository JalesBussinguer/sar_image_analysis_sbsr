# SAR Image Analysis for SBSR

Este repositório reúne o código, dados e documentos de um estudo de análise de imagens SAR para avaliar homogeneidade espacial de classes de vegetação no Cerrado brasileiro, usando dados de NISAR e Sentinel-1.

O projeto concentra-se na análise de intensidade de sinais SAR nas bandas HH e HV, com foco em estatísticas de amostragem, número equivalente de looks (ENL), testes de homogeneidade e comparação entre classes e sensores.

## Objetivo

Investigar se amostras de uma mesma classe de cobertura do solo apresentam comportamento homogêneo no domínio espacial e avaliar como diferentes parametrizações e sensores influenciam a modelagem da intensidade SAR.

## Principais componentes

- Análises em Quarto/HTML para NISAR e Sentinel-1:
  - `nisar_index.qmd`
  - `sentinel1_index.qmd`
- Script para extração de pixels por amostra e comparação de pares de intensidade:
  - `Code/extract_tiff_pixel_pairs_to_csv.py`
- Script para extração de amostras e cálculo de ENL por região:
  - `Code/extract_nisar_enl_samples.py`
- Dados geoespaciais e tabelas de amostras em:
  - `Data/`
- Figuras e ilustrações em:
  - `Figures/`
- Resultados e saídas geradas em:
  - `Outputs/`
- Textos e materiais do manuscrito em:
  - `Text/`

## Estrutura do projeto

```text
.
├── README.md
├── nisar_index.qmd
├── sentinel1_index.qmd
├── references.bib
├── Code/
│   ├── extract_nisar_enl_samples.py
│   ├── extract_tiff_pixel_pairs_to_csv.py
│   └── extract_tiff_pixel_pairs_to_csv.config.json
├── Data/
│   ├── homogeneity_samples_sbsr_bsb_200_samples.geojson
│   ├── homogeneity_samples_sbsr_bsb_300_samples.geojson
│   ├── nisar_ENL_samples/
│   ├── pnb_samples/
│   └── sentinel1_ENL_samples/
├── Figures/
├── Images/
├── Outputs/
├── Tests/
├── Text/
└── ...
```

## Fluxo de uso

1. Prepare os dados SAR e os arquivos de amostras geoespaciais em `Data/`.
2. Extraia os pixels por polígonos de amostra com o script de extração:

```bash
python Code/extract_tiff_pixel_pairs_to_csv.py
```

3. Estime o ENL por amostra e para a cena com:

```bash
python Code/extract_nisar_enl_samples.py
```

4. Abra os relatórios Quarto para reproduzir a análise e as figuras:

```bash
quarto render nisar_index.qmd
quarto render sentinel1_index.qmd
```

## Requisitos

- Python 3
- GeoPandas
- Rasterio
- NumPy
- Shapely
- tqdm
- R + Quarto para renderização dos arquivos `.qmd`
- Pacotes R usados na análise estatística, como `ggplot2`, `ggthemes`, `readr`, `reshape2` e `twosamples`

## Observações

Este repositório foi organizado para apoiar a reprodução de experimentos de análise estatística e geoespacial em imagens SAR, com foco em amostras de vegetação nativa do Cerrado e comparações entre classes e sensores.

A documentação principal do estudo está em `nisar_index.qmd` e `sentinel1_index.qmd`, enquanto os resultados e dados de apoio ficam em `Data/`, `Figures/` e `Outputs/`.

## Licença

A licença do projeto deve ser definida conforme a política do grupo de pesquisa ou da instituição responsável. Se necessário, adicione um arquivo `LICENSE` ao repositório.