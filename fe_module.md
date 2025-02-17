# 前端模块化

## 规范
规范包含：
- commonJs (cjs) 主要用于node环境，不可用于浏览器环境
- amd 异步模块加载方案实现，主要用于浏览器环境
- cmd 类amd，依赖后置，执行时按需加载依赖
- umd 提供通用导入导出，兼容 commonjs、amd
- ES Module (esm) 现代的标准的前端模块化规范，不限环境

使用的模块规范，影响产出的js产物的模块规范，但不强关联执行环境，如esm可同时为node、浏览器环境使用；

## 编译

编译时，设定的 package.json 里的 type 指定的是 **语法规范**，即使用commonJs还是es module；

commonJs 与 es module 分别可以使用对应的文件尾追

commonJs -> index.cjs
es module -> index.mjs

带尾缀的优先级高于普通js尾缀文件。

同时，main、module、exports、browser分别都是用于指定当前仓库的导出，不同的字段控制的精度还有优先级不同，同时可以通过这些字段来指定不同环境的导出文件。

main -> 定义npm包入口文件，browser与node环境通用
module -> 定义npm包的esm规范的入口文件，browser与node环境通用
browser -> 定义npm包在browser环境下的入口文件
exports -> 无关运行时环境，语言/文件层面的导出映射

忽略文件尾缀导致的优先级，语法映射优先级（exports） > browser > module > main
当使用了特殊文件尾缀（mjs、cjs）时，这个优先级最高


