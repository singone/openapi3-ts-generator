## 介绍
[![GitHub Repo stars](https://img.shields.io/github/stars/singone/openapi3-ts-generator?style=social)](https://github.com/singone/openapi3-ts-generator.git)
[![npm (scoped)](https://img.shields.io/npm/v/openapi3-generator-ts)](https://www.npmjs.com/package/openapi3-generator-ts)
![GitHub tag (latest SemVer pre-release)](https://img.shields.io/github/v/tag/singone/openapi3-ts-generator?include_prereleases)

根据 [OpenApi3](https://swagger.io/blog/news/whats-new-in-openapi-3-0/) 文档生成 request 请求代码。

## 使用
```node
npm i --save-dev openapi3-generator-ts
```
在项目根目录新建 ```openapi.config.ts```
```ts
const { generateService } = require('openapi3-ts-generator')

generateService({
  schemaPath: 'http://petstore.swagger.io/v2/swagger.json',
  servicesPath: './services',
  beforeData(openAPI) {
    // todo 修改参数
    return openAPI;  
  },
})

```
在 ```package.json``` 的 ```script``` 中添加 openapi: 
```
"openapi": "node openapi.config.ts",
```

生成api
```node
npm run openapi
```
## 参数
|  属性   | 必填  | 备注 | 类型 | 默认值 |
|  ----  | ----  |  ----  |  ----  | - |
| requestLibPath  | 否 | 自定义请求方法路径 | string | - |
| requestImportStatement  | 否 | 自定义请求方法表达式 | string | - |
| apiPrefix  | 否 | api 的前缀 | string | - |
| servicesPath  | 否 | 生成的文件夹的路径 | string | - |
| schemaPath  | 否 | openAPI 3.0 的地址 | string | - |
| projectName  | 否 | 项目名称 | string | - |
| namespace  | 否 | 类型命名空间名称 | string | APITypes |
| mockPath  | 否 | mock目录 | string | - |
| enumStyle  | 否 | 枚举样式 | string-literal \| enum | string-literal |

