# A project to learn component development

## 准备工作

### (一)初始化项目

##### 1、我们使用 pnpm 进行包管理，首先进行项目初始化

```bash
pnpm init
pnpm add typescript eslint @mistjs/eslint-config-vue-jsx prettier -D
```

##### 2、打开项目文件夹，创建.gitignore 文件,输入需要上传省略的文件。。。

##### 3、初始化 git

### （二）配置 ts 和单测配置

#### 安装依赖

```bash
pnpm add @mistjs/tsconfig-vue -D
```

#### 创建 tsconfig.json

```json
{
  "extends": "@mistjs/tsconfig-vue"
}
```

#### 安装测试和打包依赖

```bash
pnpm add vitest vite -D
```
### (三)代码提交规范
#### 安装依赖
```bash
pnpm add @commitlint/cli @mistjs/tsconfig @commitlint/config-conventional husky  -D
```
#### 创建.commitlintrc文件
```json
{
    "extends": [
      "@commitlint/config-conventional"
    ],
    "rules": {
      "type-enum": [
        2,
        "always",
        [
          "feat",
          "fix",
          "refactor",
          "test",
          "build",
          "docs",
          "chore"
        ]
      ],
      "subject-max-length": [1,"always", 150]
    }
}
```
#### 修改package.json文件并且执行命令
```json
{
 "scripts": {
    "test": "vitest",
    "prepare":"husky install"
  },
}
```
And
```bash
pnpm prepare
```
#### 执行命令，创建钩子文件
```pnpm
pnpm exec husky add .husky/commit-msg " pnpm exec commitlint -e \"$1\""   

```
文件内容为（可能会修改文件）
```bash
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"
pnpm exec commitlint -e "$1"
```
#### 配置代码提交错误规范
