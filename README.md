# LaTex-CN
LaTex常见编辑器汇总：优缺点及配置教程 （Texlive/VSCode/Overleaf）

---

# 1. VSCode+Texlive+LaTeX Workshop+Copilot AI辅助写作 （推荐）
## 1.1. 安装及配置教程
### 1.1.1 安装texlive
- 安装参考链接： https://www.bilibili.com/read/cv6966909?from=search
- Texlive 清华镜像 https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/
### 1.1.2 安装vscode
- 安装LaTeX Workshop插件 
- 安装LTeX插件（拼写检查）
### 1.1.3 修改vscode的配置文件，设置编译程序
**！！！简单使用不需要进行下方配置**


打开settings.json： 左下角“设置”按钮 --> Command Palette --> Preferences: Open User Settings (JSON). （https://www.jb51.net/softjc/730336.html） 
``` 
"latex-workshop.latex.tools": [
     {
         "name": "xelatex",
         "command": "xelatex",
         "args": [
           "-synctex=1",
           "-interaction=nonstopmode",
           "-file-line-error",
           "%DOC%"
         ]
     },
     {
         "name": "pdflatex",
         "command": "pdflatex",
         "args": [
           "-synctex=1",
           "-interaction=nonstopmode",
           "-file-line-error",
           "%DOC%"
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
   {
     "name": "pdflatex -> bibtex -> pdflatex*2",
     "tools": [
       "pdflatex",
       "bibtex",
       "pdflatex",
       "pdflatex"
     ]
   },
     {
       "name": "XeLaTeX",
       "tools": [
         "xelatex"
       ]
     },
     {
       "name": "PDFLaTeX",
       "tools": [
         "pdflatex"
       ]
     }, 
     {
       "name": "latexmk",
       "tools": [
         "latexmk"
       ]
     },
     {
       "name": "BibTeX",
       "tools": [
         "bibtex"
       ]
     },
     {
       "name": "xelatex -> bibtex -> xelatex*2",
       "tools": [
         "xelatex",
         "bibtex",
         "xelatex",
         "xelatex"
       ]
     }
 ],
 ```


### 1.1.4 预览及同步(LaTeX Workshop自带，不需要配置)
**！！！最新版本的LaTeX Workshop，可以浏览器作为pdf viewer并自带同步功能，不需要配置安装**
- 亲测使用Edge浏览器可以作为pdf viewer，
- latex到pdf前向同步：ctrl+alt+j ( Mac上cmd+option+j)
- pdf到latex反向同步：Control+鼠标左键 （Mac上是Command+鼠标左键）

以下是**旧版本**的windows上安装SumatraPDF用于预览pdf和反向搜索，新版本不需要配置，仅供参考
```

# windows 安装SumatraPDF用于预览pdf
（https://blog.csdn.net/yuehenmiss/article/details/102915332
https://github.com/James-Yu/LaTeX-Workshop/wiki/View#using-synctex-with-an-external-viewer）
 
# 1. Vscode中设置SumatraPDF用于预览pdf
"latex-workshop.view.pdf.viewer": "external",
"latex-workshop.view.pdf.ref.viewer":"external",
"latex-workshop.view.pdf.external.viewer.command": "C:/Users/gyguo/AppData/Local/SumatraPDF/SumatraPDF.exe",
"latex-workshop.view.pdf.external.viewer.args": ["%PDF%"],
Vscode中设置正向搜索（vscode到SumatraPDF），注意修改为自己的地址
"latex-workshop.view.pdf.external.synctex.command": "C:/Users/gyguo/AppData/Local/SumatraPDF/SumatraPDF.exe",
"latex-workshop.view.pdf.external.synctex.args": [
 "-forward-search",
 "%TEX%",
 "%LINE%",
 "%PDF%"
 ],

# 2. SumatraPDF中设置反向搜索(SumatraPDF到vscode) 
2.1. 进入设置->选项->设置反向搜索命令行
"Code.exe" "resources\app\out\cli.js" --ms-enable-electron-run-as-node -r -g "%f":"%l"

2.2. 根据 VSCode 具体的安装位置将Code.exe和 resources\app\out\cli.js 换成 VSCode 在自己的电脑上的安装位置，例如 C:\Users\gyguo\AppData\Local\Programs\Microsoft VS Code\Code.exe 以及 C:\Users\gyguo\AppData\Local\Programs\Microsoft VS Code\resources\app\out\cli.js 
"C:\Users\gyguo\AppData\Local\Programs\Microsoft VS Code\Code.exe" "C:\Users\gyguo\AppData\Local\Programs\Microsoft VS Code\resources\app\out\cli.js" --ms-enable-electron-run-as-node -r -g "%f":"%l"

如果找不到设置反向搜索命令行选项，打开SumatraPDF-->点击左上角三条杠设置，高级选项，在代码末尾插入两条代码
InverseSearchCmdLine = "C:\Users\gyguo\AppData\Local\Programs\Microsoft VS Code\Code.exe" "C:\Users\gyguo\AppData\Local\Programs\Microsoft VS Code\resources\app\out\cli.js" --ms-enable-electron-run-as-node -r -g "%f":"%l"
EnableTeXEnhancements = true
```

### 1.1.5 安装Github copilot或者通义灵码等插件 


## 1.2. 优缺点
- 优点： 可以结合多种插件扩展性比较强。比如可随时同步GitHub，结合overleaf使用实现在线编辑和本地编辑的同步；或者结合Zotero实现参考文献直接插入；可以使用Github Copilot或者通义灵码等插件实现辅助写作。
- 缺点： 整体配置比较麻烦 （新版本已经大幅度改进）

# 2. Texlive + Texstudio
## 2.1 安装及配置
- 安装参考链接： https://www.bilibili.com/read/cv6966909?from=search
- Texlive 清华镜像 https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/
## 2.2 优缺点
- 优点：安装简单，定期更新，功能完善，界面优美
- 缺点：中文支持不好

# 3. Overleaf 在线版编辑
Overleaf
## 3.1. 优缺点
- 优点：在线编译，不限设备随时查看，支持多人编辑
- 缺点：编译较慢，调试bug较难


# 4. VSCode+ github+overleaf 
## 4.1. 使用逻辑 
- 本地编写用vscode编写完成后上传到github，在线overleaf编辑时通过github同步
- overleaf编辑后同步到github，通过github下载到本地  
## 4.2. 安装及配置教程
- 安装配置  VSCode + Texlive + LaTeXWorkshop
- 官网下载 Git windows 安装包，https://git-scm.com/download/win， 然后点击安装
- 将overleaf中新建project，文件同步到github上面（新用户需要会员）
- 在vscode左侧打开在github中库托管的文件夹，用github登录VSCode，从github clone 本地文件
- 本地修改的文件可以提交到github上面，overleaf随时可从github上同步  
## 4.3. 优缺点 
- 优点： 可以轻松实现在线编辑和本地编辑之间的同步
- 缺点： 整体流程较多，多人协同时容易覆盖。


# 5. CTEX（不推荐）
## 5.1 安装及配置
- 下载ctex直接安装： http://www.ctex.org/CTeXDownload
## 5.2 优缺点
- 优点：中文支持比较好
- 缺点：很久没有更新版本，界面比较古老


