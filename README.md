## Project Description
This code is released to complement the following publication

[*Chuklin, A. and de Rijke, M. 2016. Incorporating Clicks, Attention and Satisfaction into a Search Engine Result Page Evaluation Model. CIKM (2016).*](https://research.google.com/pubs/archive/45562.pdf)

This is not an official Google product.

It has several components described below:
  
  * `logs_collection/` — JavaScript library to proxy your request to a search engine and log your actions;
  * `logs_management/` — AppEngine application to save the search log and provide the user with a way to redact their logs;
  * `logs_processing/` — collection of Python scripts to process the logs exported from the logs management app and the crowdsourcing platform;
  * `rating_collection/`– templates to collect ratings from [CrowdFlower](https://www.crowdflower.com/). If you work with another crowdsourcing platform, you'll have to adapt the templates. We had to work with CrowdFlower, because it's, to the best of our knowledge, the only crowdsourcing platform available outside the US. We wish there were a better choice.
  * `data_analysis/` – collection of [Jupyter / iPython](http://jupyter.org/) notebooks to slice and dice the data.


## Requirements

### Logs Colection via Proxy
See `logs_collection/README.md`.

### App Engine log_management App

*  Python libraries:

```
pip install -t logs_management/lib Flask GoogleAppEngineCloudStorageClient Werkzeug
```

* [Bootstarp Datepicker](https://github.com/eternicode/bootstrap-datepicker/), tested with version retrieved on 09.11.2014:
  * CSS file to be put in `logs_management/static/css/datepicker.css`
  * JS file to be put in `logs_management/static/js/bootstra-datepicker.js`
* [Bootstarp DatePaginator](https://github.com/jonmiles/bootstrap-datepaginator), tested with v1.1.0:
  * JS file to be put in `logs_management/static/js/bootstra-datepaginator.js`
* [Moment JS](http://momentjs.com/), the version required by the Bootstrap DatePaginator
  * JS file to be put in `logs_management/static/js/moment.js`
* (Optional) Ajax loader gif generated via [ajaxload.info](http://www.ajaxload.info/):
  * Go to website, select indicator type "Bar", press "Generate it" download it.
  * Put it under `logs_management/static/img/ajax-loader.gif`
  * You can use other image (or none at all) if you wish.
  
### Logs Processing / Data Analysis
* Scientific Python stack: NumPy, SciPy, Pandas, scikit-learn, Matplotlib, Seaborn
* [Jupyter / iPython](http://jupyter.org/)
* jsonpickle
* [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/) (not needed if working with [the anonymized dataset](http://ilps.science.uva.nl/resources/cas-eval/))
* [PyClick](https://github.com/markovi/PyClick)


## Quick Start
If you want to just play with the data do the following:
  * install the requirements for data analysis (see above)
  * download [the anonymized dataset](http://ilps.science.uva.nl/resources/cas-eval/)
  * launch `jupyter notebook` from the project directory, open [localhost:8888](http://localhost:8888) in your browser and navigate to `data_analysis/Results.ipynb`
