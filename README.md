pdf-title-rename
----------------

A batch-renaming script for PDF files based on the Title and Author information in the metadata and XMP. The XMP metadata, if available, supersedes the standard PDF metadata. The output format is currently:

    [FirstAuthorLastName [LastAuthorLastName ]- ][SanitizedTitleText].pdf

Only the article title is used if no author information is found. First and last author surnames are used if the `creator` field in the XMP is a list of more than one author. 

To use the script, simply pass in a list or glob of PDF filenames. If you want to see what it would do without changing anything, do a dry run with `-n`. There is also an interactive mode with `-i` that will let you open the files and manually enter titles and author strings if you have problematic PDFs without proper metadata.

    usage: pdf-title-rename [-h] [-n] [-i] [-d DESTINATION] files [files ...]

    PDF batch rename

    positional arguments:
      files                 list of pdf files to rename

    optional arguments:
      -h, --help            show this help message and exit
      -n                    dry-run listing of filename changes
      -i                    interactive mode
      -d DESTINATION, --dest DESTINATION
                            destination folder for renamed files

This script is intended as a first pass in an academic PDF workflow to get browsable filenames for a pile of articles that have been downloaded but not yet filed away.

- Requirements

 * [PDFMiner](https://github.com/euske/pdfminer/)
 * [xmp](http://blog.matt-swain.com/post/25650072381/a-lightweight-xmp-parser-for-extracting-pdf-metadata-in)

## PDF重命名.py 中文解析

上面是原版英文README,这里解析一下：
需要前提安装的插件有`PDFMiner`和`xmp`,最新版的`PDFMiner`包含`pdf2txt.py`,安装完将拷贝所有py文件到PYTHONPATH目录下,没有的话拷贝到python安装目录,我这里是安装anaconda所以
`C:\Users\xxxx\Anaconda3\Scripts`,前提该目录在环境变量Path里面，因此在cmd里面输入：

pdf-title-rename.py

    pdf-title-rename.py TEST.pdf

pdf2txt.py

    pdf2txt.py -o TEST.txt TEST.pdf && cat TEST.txt | head -n 10 | sed ':a;N;$!ba;s/\n/ /g'
    mv AA.pdf AA_new.pdf

## 批量重命名(推荐)

[2018.8.12] 更新添加中文支持，后期预计添加txt,word文档等重命名

pdf-title-rename-batch
----------------

fork and modified from [pdftitle.py-hanjianwei](https://gist.github.com/hanjianwei/6838974)

Depends on: [pyPDF:conda install pypdf2](https://github.com/mstamy2/PyPDF2), PDFMiner.

Usage:

    find . -name "*.pdf" |  xargs -I{} pdf-title-rename-batch.py -d tmp --rename {}

    单个文件使用: pdf-title-rename-batch.py --rename TEST.pdf

    或者 pdf-title-rename-batch.py TEST.pdf

That's all,enjoy.


