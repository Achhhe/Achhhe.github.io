---
layout:     post
title:      "vscode + latex = happy writing !"
subtitle:   "AcademicWriting头发搬家系列"
date:       2021-05-02 15:48:00
author:     "He"
header-img: "img/post-bg-2015.jpg"
tags:
    - vscode
    - latex

---

> “Yeah It's on. ”

> 新手建议使用texlive+texstudio写作，texstudio的工具栏对新手很友好，熟练后可转为vscode写作，
>
> - texstudio：适合新手；有工具栏，“加特效”便捷；环境配置方便；
>
>   容易卡死，特别是开了有道词典；无自动补全；无法统计字数，特别是中文论文写作
>
> - vscode：适合老司机；自动补全；调试方便【全局搜索真香】；插件多，各种附加功能真香，比如统计中文字数

## 基础软件安装

- [vscode](https://code.visualstudio.com/)，写作+编译，安装教程网上一大堆，跳过 :confused:
- [sumatraPDF](https://www.sumatrapdfreader.org/free-pdf-reader)， 查看pdf，安装教程网上一大堆，跳过 :confused:
- [texlive](http://mirrors.hust.edu.cn/CTAN/systems/texlive/Images/)，latex编译器，安装参考武大[黄正华老师](http://aff.whu.edu.cn/huangzh/)主页，无需装WinEdt，冲 :smiley:

## 环境配置

### vscode 插件安装

安装插件 

- latex utilities：统计中文字数
-  latex workshop：适配latex环境

其他还有很多latex插件，自行尝试吧  :confused:

### 配置json

按`f1`，搜索`setting.json`，选择`首选项：打开设置(JSON)`【注意，不是默认设置！！！】，打开`setting.json`配置文件，添加如下代码：

```latex
{
    "python.pythonPath": "D:\\Anaconda3\\pythonw.exe", //配置python路径，可有可无
    "latex-workshop.message.update.show": false,
    "latex-workshop.latex.tools": [
        {
            // 编译工具和命令
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        // {
        //     "name": "xelatex",
        //     "tools": [
        //         "xelatex"
        //     ],
        // },
        // {
        //     "name": "pdflatex",
        //     "tools": [
        //         "pdflatex"
        //     ]
        // },
        {
            "name": "xe->bib->xe->xe",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        // {
        //     "name": "pdf->bib->pdf->pdf",
        //     "tools": [
        //         "pdflatex",
        //         "bibtex",
        //         "pdflatex",
        //         "pdflatex"
        //     ]
        // }
    ],

    // "latex-workshop.view.pdf.viewer": "external",
    "latex-workshop.view.pdf.viewer": "external",

    "latex-workshop.view.pdf.external.viewer.command": "D:/SumatraPDF/SumatraPDF.exe",
    "latex-workshop.view.pdf.external.viewer.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "-reuse-instance",
        "-inverse-search",
        "\"C:/Program Files (x86)/Microsoft VS Code/Code.exe\" \"C:/Program Files (x86)/Microsoft VS Code/resources/app/out/cli.js\" -gr \"%f\":\"%l\"",
        "%PDF%"
    ],
    "files.autoSave": "off",
    "latex-workshop.view.pdf.external.synctex.command": "D:/SumatraPDF/SumatraPDF.exe",
    "latex-workshop.view.pdf.external.synctex.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "-reuse-instance",
        "-inverse-search",
        "\"C:/Users/22383/AppData/Local/Programs/Microsoft VS Code/Code.exe\" \"C:/Users/22383/AppData/Local/Programs/Microsoft VS Code/resources/app/out/cli.js\" -gr \"%f\":\"%l\"",
        "%PDF%",
    ],
    "editor.wordWrap": "on",
    "window.menuBarVisibility": "visible",
    "latex-utilities.message.update.show": false,
    "workbench.colorTheme": "Visual Studio Dark",  
}
```

**注意**！！！！！

- 要把`SumatraPDF`和`vscode`的路径修改为自己的！！！！！！
- 路径中斜线为 `/`，不是`\`！！！！

## 辅助链接

- [表格生成器](https://www.tablesgenerator.com/)
- [markdown表情包](https://blog.csdn.net/qq_40896997/article/details/106551767)
- [overleaf latex模板](https://www.overleaf.com/latex/templates)
- [latex模板](http://www.latextemplates.com/)
- [beamer模板](https://deic-web.uab.cat/~iblanes/beamer_gallery/index_by_theme.html)
- [beamer中文手册](http://static.latexstudio.net/wp-content/uploads/2017/02/BeamerUserGuide_V3.24_zh-cn.pdf)
- Todo​ :v: