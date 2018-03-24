---
layout: post
title: 规范 Git Commit Message 格式
categories: git
---

<!-- TOC -->

- [常规提交规范](#%E5%B8%B8%E8%A7%84%E6%8F%90%E4%BA%A4%E8%A7%84%E8%8C%83)
- [工具](#%E5%B7%A5%E5%85%B7)
- [安装](#%E5%AE%89%E8%A3%85)
- [参考资料](#%E5%8F%82%E8%80%83%E8%B5%84%E6%96%99)

<!-- /TOC -->

# 常规提交规范

[Angular convention](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit)

[Conventional Commits](https://conventionalcommits.org)

# 工具

[NodeJS](https://nodejs.org/en/)

以下工具组都是基于nodejs来开发的，所以需要先安装nodejs.

[commitizen](https://github.com/commitizen/cz-cli)

按照规范格式来填空，提供可执行工具，另外还要搭配commitizen adapter（即规范的定义，是commitizen的扩展）来使用，
commitizen会按照adapter的定义来给出提示，让开发者完成填空；
有开源出来已经定义好的规范，也根据工程类型可以自定义规范，前期可以先用开源的规范(e.g. cn-conventiona-changelog)

[commitlint](https://github.com/marionebl/commitlint) + [husky](https://github.com/typicode/husky/tree/master)

commitlint检查commit message是否符合规范, husky则可以勾住git，让git commit这样的动作强制去跑commitlint，避免自己有时偷懒。

[standard-version]()

可以根据commit message来生成change log。

# 安装

安装完nodejs后，进入工程根目录：

``` shell
npm init --yes 
```

会生成默认的package.json文件。

我习惯把commitizen安装到全局:

``` shell
npm i -g commitizen
```

将cz-conventional-changelog安装到工程目录下，不同的工程可选择不同的adapter:

``` shell
commitizen init cz-conventional-changelog -D -E
```


接着，安装commitlint及其*检查文件*，commitlint会根据这个*检查文件*完成检查：

``` shell
npm i -D @commitlint/config-cli @commitlint/config-conventional
```

完成后再手动生成配置文件：

``` shell
echo "module.exports = {extends: ['@commitlint/config-conventional']};" > commitlint.config.js
```

完成后需要手动到package.json里去配置一下：

``` json
{
    "scripts": {
        "commitmsg": "commitlint -e $GIT_PARAMS"
    }
}
```

将husky安装到工程目录，强制在此工程下一定要按照规范来commit:

``` shell
npm i -D husky
```

最后，还可以选择安装一下standard-version：

``` shell
npm i -D standard-version
```

完成后需要手动到package.json时去配置一下：

``` json
{
    "scripts": {
        "release": "standard-version"
    }
}
```

所有安装完成后，你的工程根目录会多出下面这些东西：

``` shell
├── commitlint.config.js
├── node_modules
└── package.json
```

package.json大致会增加以下内容：

``` json
{
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "commitmsg": "commitlint -e $GIT_PARAMS",
    "release": "standard-version"
  },
  "devDependencies": {
    "@commitlint/cli": "^6.1.3",
    "@commitlint/config-conventional": "^6.1.3",
    "cz-conventional-changelog": "^2.1.0",
    "husky": "^0.14.3",
    "standard-version": "^4.3.0"
  },
  "config": {
    "commitizen": {
      "path": "cz-conventional-changelog"
    }
  }
}
```

如果是团队协作开发，可以将package.json和comitlint.config.js提交上去，让其它成员

``` shell
npm i
```

安装后，协助大家按照相同的规范来提交代码。

# 参考资料

[优雅的提交你的 Git Commit Message](https://zhuanlan.zhihu.com/p/34223150)


