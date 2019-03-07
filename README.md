# vuepress-theme-x

VuePress 主题。

[点击预览](http://h69.github.io)

[![npm package](https://nodei.co/npm/vuepress-theme-x.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/vuepress-theme-x)


## 起步
```
npm install vuepress-theme-x --save
```

## 使用
在 `.vuepress` 下的 `config.js` 里增加以下字段即可：
```JavaScript
module.exports = {
  ...
  theme: 'x',
  ...
}
``` 

## 范例
```
.
└── docs 
    ├── .vuepress 
    |   └── config.js
    ├── Tag 1
    |   └── Document 1
    |       └── README.md
    ├── Tag 2
    |   └── Document 2
    |       └── README.md
    └── README.md 
```

```JavaScript
// config.js
module.exports = {
  title: 'x',
  theme: 'x',
  themeConfig: {
    editLinkText: '编辑',
    editLinks: true,
    repo: 'your username/your repo',
    nav: [
      {
        text: 'github',
        link: 'https://github.com',
      }
    ],
    sidebar: {
      '/': [
        {
          title: 'Tag 1',
          children: [
            '/Tag 1/Document 1/',
          ],
        },
        {
          title: 'Tag 2',
          children: [
            '/Tag 2/Document 2/',
          ],
        },
      ],
    },
  },
}
```
![](./vuepress-theme-x.png)
