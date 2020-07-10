# Welcome to My World

## **This is a beautiful world,this is my world**

❤️This is a simple record of learning bits and pieces , so that each step of learning into an unforgettable memory.

❤️To improve my writing skills

❤️The future is promising



## **Introduction**

😶😐🤨🤨🙂😀😀😄😋

The world hides my learning notes, including machine learning, in-depth learning, and of course, algorithm —— the soul , welcome  small partners to visit, if there are shortcomings, please come forward, I will accept and accept your suggestions with open heart



## **Theme  Color **

### **Dominant Color**

> 默认为 `white`

点击色块可更换主题的主色

<div id="color-button">
<button data-md-color-primary="red">Red</button>
<button data-md-color-primary="pink">Pink</button>
<button data-md-color-primary="purple">Purple</button>
<button data-md-color-primary="deep-purple">Deep Purple</button>
<button data-md-color-primary="indigo">Indigo</button>
<button data-md-color-primary="blue">Blue</button>
<button data-md-color-primary="light-blue">Light Blue</button>
<button data-md-color-primary="cyan">Cyan</button>
<button data-md-color-primary="teal">Teal</button>
<button data-md-color-primary="green">Green</button>
<button data-md-color-primary="light-green">Light Green</button>
<button data-md-color-primary="lime">Lime</button>
<button data-md-color-primary="yellow">Yellow</button>
<button data-md-color-primary="amber">Amber</button>
<button data-md-color-primary="orange">Orange</button>
<button data-md-color-primary="deep-orange">Deep Orange</button>
<button data-md-color-primary="brown">Brown</button>
<button data-md-color-primary="grey">Grey</button>
<button data-md-color-primary="blue-grey">Blue Grey</button>
<button data-md-color-primary="white">White</button>
</div>

<script>
  var buttons = document.querySelectorAll("button[data-md-color-primary]");
  Array.prototype.forEach.call(buttons, function(button) {
    button.addEventListener("click", function() {
      document.body.dataset.mdColorPrimary = this.dataset.mdColorPrimary;
      localStorage.setItem("data-md-color-primary",this.dataset.mdColorPrimary);
    })
  })
</script>





### Auxiliary Colour

> 默认为 `red`

点击色块更换主题的辅助色



<div id="color-button">
<button data-md-color-accent="red">Red</button>
<button data-md-color-accent="pink">Pink</button>
<button data-md-color-accent="purple">Purple</button>
<button data-md-color-accent="deep-purple">Deep Purple</button>
<button data-md-color-accent="indigo">Indigo</button>
<button data-md-color-accent="blue">Blue</button>
<button data-md-color-accent="light-blue">Light Blue</button>
<button data-md-color-accent="cyan">Cyan</button>
<button data-md-color-accent="teal">Teal</button>
<button data-md-color-accent="green">Green</button>
<button data-md-color-accent="light-green">Light Green</button>
<button data-md-color-accent="lime">Lime</button>
<button data-md-color-accent="yellow">Yellow</button>
<button data-md-color-accent="amber">Amber</button>
<button data-md-color-accent="orange">Orange</button>
<button data-md-color-accent="deep-orange">Deep Orange</button>
</div>
<script>
  var buttons = document.querySelectorAll("button[data-md-color-accent]");
  Array.prototype.forEach.call(buttons, function(button) {
    button.addEventListener("click", function() {
      document.body.dataset.mdColorAccent = this.dataset.mdColorAccent;
      localStorage.setItem("data-md-color-accent",this.dataset.mdColorAccent);
    })
  })

  // #758
  document.getElementsByClassName('md-nav__title')[1].click()
</script>



## **MkDocs  Environmental Description**

------

- python: 3.6.6

- 依赖的python包:

  | 包名               | 模块名   | 版本  |
  | ------------------ | -------- | ----- |
  | mkdocs             | mkdocs   | 1.0.4 |
  | mkdocs-material    | material | 3.0.6 |
  | Markdown           | markdown | 3.0.1 |
  | pymdown-extensions | pymdownx | 6.0   |

## **mkdocs-material Deploy**

------

### **Install**

```
pip install mkdocs mkdocs-material
```



### **Initialization Project**

```
mkdocs new my-project
```

The my-project directory is generated, and when you enter it, you can see that some files, including mkdocs.yml, are placed by default, which is the main configuration file.

### **Modify the Theme**

In mkdocs.yml add:

```
theme:
  name: material
```

### **Add Pages**

In mkdocs.yml add:

```
nav:
  - 介绍: index.md
  - 安装:
      - 本地环境搭建: install/local.md
      - 发布至GitHub Pages: install/github-pages.md
      - 发布至自己的HTTP Server: install/http-server.md
  - 语法:
      - 语法总览: syntax/main.md
      - 标题: syntax/headline.md
      - 段落: syntax/paragraph.md
```

### **Adding Extensions**

In mkdocs.yml add:

```
markdown_extensions:
  - admonition
  - codehilite:
      guess_lang: false
      linenums: false
  - toc:
      permalink: true
  - footnotes
  - meta
  - def_list
  - pymdownx.arithmatex
  - pymdownx.betterem:
      smart_enable: all
  - pymdownx.caret
  - pymdownx.critic
  - pymdownx.details
  - pymdownx.emoji:
      emoji_generator: !!python/name:pymdownx.emoji.to_png
  - pymdownx.inlinehilite
  - pymdownx.magiclink
  - pymdownx.mark
  - pymdownx.smartsymbols
  - pymdownx.superfences
  - pymdownx.tasklist
  - pymdownx.tilde
```

### **Mkdocs Service Startup**

```
# 在my-project目录里执行
mkdocs serve
```

Open through the browser to see the effect <http://127.0.0.1:8000/> 









### Learn more

You can visit [Mkdocs-github pages](https://my.oschina.net/fzxiaomange/blog/3010921). Of course [mkdocs-material](https://squidfunk.github.io/mkdocs-material/getting-started/) is good!