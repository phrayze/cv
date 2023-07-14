# Markdown CV

This repo contains my CV in Markdown files, which can be published to HTML, PDF and DOC formats.
Requirements to execute are
* pandoc
* wkhtmltopdf

Pandoc: allows you to convert any file to html or doc
wkhtmltopdf: takes a html output and prints it to pdf

The inspiration for this project came from having to manually edit a CV in a marked up document editor (eg Google Docs or Microsoft Word). I simply wanted to write my CV in an easily readable and highly extensible format (i.e. Markdown), and then parse it through a CSS style sheet to build a beautiful, marked up document.

# Workflow

The workflow is pretty simple.

1. Edit the .md Markdown files in the directory. Each file refers to a different section and are numbered for order.
2. Edit the includes.txt to determine the order in which your files will be parsed
3. Run pandoc to convert the Markdown file to HTML. OR DOC
4. Run pandoc to convert the Markdown file into a PDF.

# Instructions

## Pre-Requisites
Assuming you have the appropriate package installers for your operating system
* MacOS: brew
* Windows: chocalatey
  
### [Pandoc](https://pandoc.org) a universal document converter
#### MacOS
```
    brew install pandoc
```
#### Windows
```
    choco install pandoc
```

### [Wkhtmltopdf](https://wkhtmltopdf.org) convert html to pdf
#### MacOS
```
    brew install wkhtmltopdf
```
#### Windows
```
    choco install wkhtmltopdf
```

## Export MD files into includes.txt
#### MacOS
```
```
#### Windows
```
dir -name *.md -exclude README.md > includes.txt
```

## Generating Output Files

### Markdown to HTML

```
pandoc -s $(cat includes.txt) -f markdown -t html -c cv-stylesheet.css -o cv.html
```
### Markdown to DOC

```
pandoc -s $(cat includes.txt) -f markdown -t docx -c cv-stylesheet.css -o cv.doc
```
## Markdown to PDF

```
pandoc -s $(cat includes.txt) -f markdown -t pdf --pdf-engine=wkhtmltopdf -c cv-stylesheet.css -o cv.pdf
```
## Automating CV Generation
A github workflow create-cv.yml is provided which will 
* install pandoc
* install wkhtmltopdf
* convert cv in markdown format to HTML, DOC and PDF formats
* create a zip file called <github.username>-cv.zip
* the file is available to download directly from your workflow run (if completes successfully)


### TODO
- Update the workflow to generate a github page with the CV, and publish the doc / pdf to a web location for easy download