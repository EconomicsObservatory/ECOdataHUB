<div align="left"><img src="https://raw.githubusercontent.com/EconomicsObservatory/economicsobservatory.github.io/main/EO-Logo.png" width="800"/></div>

# Economics Observatory  Data Hub

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/EconomicsObservatory/ecovisualisations/blob/main/LICENSE)
![GitHub last commit](https://img.shields.io/github/last-commit/EconomicsObservatory/ECOdataHUB?label=last%20update)

[**Website**](https://www.economicsobservatory.com/)
| [**Visualisations**](https://github.com/EconomicsObservatory/ecovisualisations)
| [**Data**](https://github.com/EconomicsObservatory/ecodatahub)
|

Welcome to the **ECOdataHUB**! Here we host the our auto-updating datasets that fuel the interactive charts on the [**ECOdata dashboard**](https://economicsobservatory.github.io/ECOdataHUB/dashboard). Here you will find all the data visualisations and datasets attached to the ECOdataHUB and published on the Observatory website. Each visualisation is published under an open source [MIT licence](LICENSE), and you are free to reuse/reproduce/redistribute, with attribution. Please look at the **original** data sources for their respective data licenses and usage policy.

## 📊 Data

All of our chart data are published under their respective article [data ](https://github.com/EconomicsObservatory/ECOvisualisations/tree/main/articles/2021-04-14-a-year-in-the-uk-labour-market-whats-happened-over-the-coronavirus-pandemic/data) subfolder, but on top of that, we also operate the **[ECOdataHUB](https://github.com/EconomicsObservatory/ecodatahub)**, where you will find a trove of data used in our articles and analyses, as well as [interactive visualisation exploration interfaces](https://economicsobservatory.github.io/ECOdataHUB/dashboard). Whenever possible, we try to follow a [TIDY](http://vita.had.co.nz/papers/tidy-data.pdf) format. You can read about our data zen in [**📐data guidelines**](https://github.com/EconomicsObservatory/ECOdataHUB/tree/main/guidelines).  

Pubished | Updated | Article | Source | API | Data | Code
--- | --- | --- | --- | --- | --- | ---
2021.04.20 | 2021.04.20 | [Data Hub: Labour market](https://www.economicsobservatory.com/data-hub-labour-market) | [Office for National Statistics](https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetypes/bulletins/uklabourmarket/april2021) | [model](https://api.ons.gov.uk/timeseries/mgsx/dataset/lms/data)| [folder](/datasets/ons/lms) | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/economicsobservatory/ecodatahub/blob/main/parser.ipynb)

### Structure

You will find the datasets we curate and mirror in the [**data**](/data) folder, sorted as `provider/dataset/series`. Whenever possible, and unless absolute necessary for the visualisation, we strive to maintain a "mirror only" attitude - i.e. most of the files are direct backups of the original API call responses. Whenever new data becomes availabe, these datasets update automatically.

### Panels

Under **[panels](/panels)** each visualisation has their own (usually [Vega-lite](https://vega.github.io/vega-lite/) or [Vega](http://vega.github.io/), but sometimes a [D3plus](http://d3plus.org/) or [eCharts](https://echarts.apache.org/)) `json` specification. We normalize the data and compile the visualisations using the [**`parser.ipynb`**](/panels/lms/parser.ipynb) [Jupyter](https://jupyter.org/) notebooks. Every **panel** folder contains 3 visualisation specification files:

- In `*_eco.json` the data for the visualisation is loaded from this repository (recommended use)
- In `*_live.json` the data for the visualisation is loaded directly from its original location (e.g. [ONS API](https://developer.ons.gov.uk/)) 
- In `*_local.json` all data is stored as a static `Javascript Object` inside the `json` files (this is the *safest* but also the *slowest*)

### Embedding

Furthermore, we maintain a `viewer.html` in every **panels** folder that can take a data source parameters as its URL hash. E.g. visiting [`https://economicsobservatory.github.io/ECOdataHUB/panels/viewer.html#`**`lms/lms_eco`**](https://economicsobservatory.github.io/ECOdataHUB/panels/viewer.html#lms/lms_eco) will open the viewer for the `lms` dataset with the `eco` data source specification. **This is the recommended way** for embedding our visualisations on other sites.

## 🌌 Visualisations

Head over to our **[ECOvisualisations](https://github.com/EconomicsObservatory/ecovisualisations)** repository for all of our charts sorted by article. We try to follow industry best-practices in data visualisation and try to establish our very own visualisation guidelines for all chart types. You can read about these, as well as the tools we use in [**📐visualisation guidelines**](https://github.com/EconomicsObservatory/ECOvisualisations/tree/main/guidelines).  

## 💻 Build

We are constantly expanding the capabilities of the ECOdataHUB. To learn about the technologies used or build a similar datasets or charts like this you can follow the instructions on the [guidelines](/guidelines) page. If you discovered any bugs or have any specific suggestions or feature requests please use the [Issues](https://github.com/EconomicsObservatory/ECOdataHUB/issues) page.

## 📧 Contact

The Economics Observatory is run out of the [University of Bristol](https://www.bristol.ac.uk/) and you can read more **[about us here](https://www.economicsobservatory.com/about)**. For any technical or visualization-related questions you may contact [Dénes](mailto:d.csala@lancaster.ac.uk). For economics-related queries and anything else about the site content, or further collaborations, you may contact [Charlie](mailto:charlie.meyrick@bristol.ac.uk).

## 📰 Reference

If you would like to use the site as an information source or any of the visualizations or the data presented, you are free to do so under an [MIT licence](LICENSE) (you're free to modify anything, as long you as you mention us). Furthermore, the content of all of our articles presented on the [Economics Observatory website](https://www.economicsobservatory.com/about) is shareable under a [Creative Commons ShareAlike 4.0](http://creativecommons.org/licenses/by-sa/4.0/) license.  

If you would like to refer to it in publications or other scientific works of any kind, please use the following style:

 - `Title of article or chart`, Economics Observatory, 2021, `link to article or chart`, published on: `publication date`, accessed on: `access date`
