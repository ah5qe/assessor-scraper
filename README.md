# assessor-scraper

The goal of this project is to transform the data from the Orleans Parish
Assessor's Office [website](http://nolaassessor.com/) into a format that is
better suited for analysis.

## development environment setup

### prerequisites

You must have Python 3 installed.  You can download it
[here](https://www.python.org/downloads/).

### first setup a python [virtual environment](https://docs.python.org/3/library/venv.html#creating-virtual-environments)

```
python3 -m venv .venv
. .venv/bin/activate
```

### install the dependencies with [pip](https://pip.pypa.io/en/stable/user_guide/#requirements-files)
```
pip install -r requirements.txt
```


## Getting started

If you want to explore how to extract data using scrapy, use the [scrapy
shell](https://doc.scrapy.org/en/latest/intro/tutorial.html#extracting-data) to interactively
work with the response.

For example,
```
scrapy shell http://qpublic9.qpublic.net/la_orleans_display.php?KEY=2336-OCTAVIAST
owner = response.xpath('//td[@class="owner_value"]/text()')[0]
owner.extract()
next_page = response.xpath('//td[@class="header_link"]/a/@href').extract_first()
```

### Running the spider
Running the spider from the command line will crawl the assessors website and [output the data](https://doc.scrapy.org/en/latest/topics/feed-exports.html) to a file
format of your choice.

```
scrapy runspider scraper/spiders/assessment_spider.py -o output.csv
```
> Warning: this may take a long time...you can kill the process with ctrl+c
