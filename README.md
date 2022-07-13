# Jupyter Documentation
This repo contains code to create a PDF document from a Jupyter Notebook.

## Prerequisites
You just need Python and Docker in order to run this example.

## Create a PDF
To create a PDF out of the notebook in `notebooks/notebook.ipynb` follow these steps:
1. clone this repo
2. create a virtual python environment
3. install dependencies with `pip install -r requirements.txt`
4. convert the notebook to asciidoc with 
    ```shell
    jupyter nbconvert --to asciidoc --TemplateExporter.extra_template_basedirs=asciidoc/nbconvert --template sample_template notebooks/notebook.ipynb
    ```
5. Run asciidoctor to convert the asciidoc file to PDF:
    ```shell
    docker run --rm -v $(pwd):/documents/ asciidoctor/docker-asciidoctor:1.16 asciidoctor-pdf -a pdf-stylesdir=asciidoc -n -a pdf-style=sfl -a allow-uri-read notebook.asciidoc
    ```