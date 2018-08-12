# PDF重命名.py 

## 中文解析

原版英文README,这里解析一下：
需要前提安装的插件有`PDFMiner`和`xmp`,最新版的`PDFMiner`包含`pdf2txt.py`,安装完将拷贝所有py文件到PYTHONPATH目录下,没有的话拷贝到python安装目录,我这里是安装anaconda所以
`C:\Users\xxxx\Anaconda3\Scripts`,前提该目录在环境变量Path里面，因此在cmd里面输入：

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


