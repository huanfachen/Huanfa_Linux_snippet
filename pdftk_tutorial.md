# PDF tasks using pdftk command-line

PDFtk is a simple tool for doing everyday things with PDF documents. It comes in three flavors: *PDFtk Free*, *PDFtk Pro*, and our original command-line tool [*PDFtk Server*](https://www.pdflabs.com/tools/pdftk-server/).

To install pdftk on Linux, use ''

Below are some common PDF tasks and solutions:

1. Join in1.pdf and in2.pdf into a new PDF, out1.pdf

   ``` pdftk in1.pdf in2.pdf cat output out1.pdf```

2. Remove page 13 from in1.pdf to create out1.pdf

   ```pdftk in1.pdf cat 1-12 14-end output out1.pdf``` or:

   ```pdftk A=in1.pdf cat A1-12 A14-end output out1.pdf```

3. Extract the first two pages from two documents in1.pdf and in2.pdf and combine them into out1.pdf

   ```pdftk A=in1.pdf B=in2.pdf cat A1-2 B1-2 output out1.pdf```

4. Extract page 1-2 from in1.pdf to create out1.pdf

   ```pdftk in1.pdf cat 1-2 output out1.pdf```

5. Split a single input pdf into individual pages (and create a report txt) (by default, the output file are named pg_%04d.pdf, e.g. pg_0001.pdf)

   ```pdftk in1.pdf burst``` , or to custom page names,

   ```pdftk in1.pdf burst output page_%04d.pdf``` 

7. Count the number of words in a pdf (Note: pdftotext is not part of pdftk; to install this function in Linux Ubuntu, using *sudo apt-get install poppler-utils*)

   ```pdftotext myfile.pdf - | wc -w```



- References

[PDFtk Server Examples](https://www.pdflabs.com/docs/pdftk-cli-examples/)

[PDF Labs](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/)

[PDFtk Server Manual](https://www.pdflabs.com/docs/pdftk-man-page/)

[pdftotext man](https://linux.die.net/man/1/pdftotext)