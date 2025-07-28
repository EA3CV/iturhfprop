# iturhfprop

Repositorio Dockerizado para predicción HF utilizando [iturhfprop](https://www.itu.int/en/ITU-R/study-groups/rsg3/Pages/HF-Prop.aspx) como motor de cálculo.

## Características

- Predicción de propagación HF vía API REST (`Flask`)
- Soporte para:
  - Línea gris
  - PSKReporter
  - RBN y Telnet
  - Redis como caché
- Configurable vía `config.json`

## Uso

Clona el repositorio:

```bash
git clone https://github.com/EA3CV/iturhfprop.git
cd iturhfprop
