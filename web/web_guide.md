# Web前端开发标准规范归纳
Web前端作为开发团队中不可或缺的一部分，需要按照相关规定进行合理编写（一部分不良习惯可能给自己和他人造成不必要的麻烦）。不同公司不同团队具有不同的规范和文档。下面是根据不同企业和团队的要求进行整理的结果。

---
[基础规范](#基础规范)   
[项目结构规范例](#项目结构规范例)   
[HTML规范](#html规范)   
[CSS规范](#css规范)   
[JS规范](#js规范)   
[编辑器插件](#编辑器插件)   
[参考目录](#参考目录)   

## 基础规范
>   坚持制定好的代码规范。  
>   无论团队人数多少，代码应该同出一门。  
>   如果你想要为这个规范做贡献或觉得有不合理的地方,请及时提出。
-   文件夹命名规范：    
    采用驼峰命名方式，尽量用英文见名知意； “例：`chartFilter`”
-   文件命名规范：  
    -   使用小写字母；如：`index.html`
    -   多个单词时，用下划线连接；如：`person_center.html`
    -   **某些说明书文件的文件名，可以使用大写字母，如`README`、`LICENSE`等，方便区分**
-   html、css命名规范：    
    -   类名使用小写，以中线分隔；“例：`element-content`”  
    -   id采用驼峰式命名；“例：`myDialog `” 
-   JavaScript命名规范：    
    -   变量命名    
        类型|范例   
        --|--
        标准变量采用驼峰式命名|`var thisIsMyName;`
        'ID'在变量名中全大写|`var goodID`
        'URL'在变量名中全大写|`var reportURL;`
        常量全大写，用下划线连接|`var MAX_COUNT = 10;`
        jquery对象必须以'$'开头命名|`var $body = $('body');`
    -   函数命名    
        **命名方式**：首字母小写驼峰式命名.如：`getData()`；
        **命名规则**：前缀为动词      
        动词|含义|返回值
        --|--|--
        can|判断是否可执行某个动作|函数返回一个布尔值。`true|false`
        has|判断是否含有某个值|函数返回一个布尔值。`true|false`
        is|判断是否为某个值|函数返回一个布尔值。`true|false`
        get|获取某个值|函数返回一个非布尔值
        set|设置某个值|无返回值、返回是否设置成功或者返回链式对象
-   注释规范   
    常用注释关键字
    注释名|语法|含义|示例
    --|--|--|--
    `@param`|`@param`参数名 {参数类型} 描述信息|描述参数的信息|`@param name {String}`传入名称
    `@return`|`@return`{返回类型} 描述信息|描述返回值的信息|`@return{Boolean}true:`可执行;`false:`不可执行
    `@auther`|`@author` 作者信息[附属信息：如日期]|描述此函数作者的信息|`@author 张三 2015/07/21`
    `@version`|`@version XX.XX.XX`|描述此函数的版本号|`@version 1.0.3`

    -   js库级别需要功能描述、作者、版本信息、更新记录[使用说明 | demo案例]     
        示例：
        ```
        /**  
            * @author sien
            * @description iframe父子页面通信之子页面接口 (单例模式)
            * @version 20180101
            * @notice 独立子页面中引入  (原生实现的功能页面,不支持动态加载js、css)
            * 2018-01-17 添加延时处理，加载完app.config.json才初始化完毕，执行子页面入口方法
            * 2018-04-10 计算子页面尺寸方法调整
        */
        ```
    -   方法级别需要功能描述、参数说明      
        示例：
        ```
        /**
            * 子页面呼叫父框架消息提示方法   [tested]
            * @param {消息内容} args 
            * @param {可手动关闭} closable 
            * @param {icon类型 or 图片地址} type 
            * @param {关闭回调函数} callback 
        */
        ```
    -   语句级别注释要描述代码实现原因 or 原理，背后的考量是什么        
        示例：
        ```
        //cp.add 20180719 解决集成到非框架页面无接口方法问题
        ```
    -   引用级别注释要描述功能
		示例：
        ```
        <!-- 城市运行样式 -->
        <!--echarts图形组件-->
        ```
    -   特殊注释：
		示例：
        ```
        // TODO 待实现内容
        <!-- 左侧布局第一层 -->   布局说明
        ```
## 项目结构规范例
-   公共文件 例：第三方插件 libs
-   用户模块 account
    -   行为脚本	js
    -   外观样式	css
    -   资源文件	imgs
    -   布局结构	当前目录(./ )
## HTML规范    
-   模板
    ```zwz
    - 使用 HTML5 的文档声明类型
    <!DOCTYPE html>
    <html lang="en">
    <head>
        // 编码格式 
        <meta charset="UTF-8">
        // 视图显示
        <meta name="viewport" content="width=device-width,initial-scale=1.0">
        // 浏览器兼容方式
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        // 页面名称
        <title>{{页面功能名称}}</title>
        // 样式文件位置
        <link rel="stylesheet" href="main.css">
    </head>
    <body>
        // 脚本文件位置，如果只兼容现代浏览器，可以把脚本文件放在上面
        <script src="main.js" async></script>
    </body>
    </html>
    ```
-   属性顺序
    属性应该按照特定的顺序出现以保证易读性；    
    **1.    class** 
    **2.    id**    
    **3.    name**  
    **4.    data-***    
    **5.    src, for, type, href, value , max-length, max, min, pattern**   
    **6.    placeholder, title, alt**   
    **7.    aria-*, role**  
    **8.    required, readonly, disabled**  
    **class**是为高可复用组件设计的，所以应处在第一位；     
    **id**更加具体且应该尽量少使用，所以将它放在第二位。
-   语义化
    >   语义化是指：根据元素其被创造出来时的初始意义来使用它。  
    -   避免只使用一种标签，如`div、span、p`      
    -   使用方便对布局理解的标签，如`header、main、article`
-   alt标签不为空   
    `<img>`标签的 alt 属性指定了替代文本，用于在图像无法显示或者用户禁用图像显示时，代替图像显示在浏览器中的内容。  
    从SEO角度考虑，浏览器的爬虫爬不到图片的内容，所以我们要有文字告诉爬虫图片的内容
    假设由于下列原因用户无法查看图像，alt 属性可以为图像提供替代的信息：    
    -   网速太慢
    -   src属性中的错误
    -   浏览器禁用的图像
    -   用户使用的是屏幕阅读器
-   减少标签数量
    在编写HTML代码时，需要尽量避免多余的父节点；
    很多时候，需要通过迭代和重构来使HTML变得更少。
-   实用高于完美
    尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；
    任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。
## CSS规范
-   书写规范（**可以使用css格式化插件**）
    -   缩进使用soft tab（4个空格）。
    -   每个属性声明末尾都要加分号。
    -   颜色16进制用小写字母如：`color: #abcdef;`；颜色16进制尽量用简写如：`color: #fff;`。
    -   省略0后面的单位
        ```
        //bad
        padding-bottom: 0px;
        margin: 0em;
        //good
        padding-bottom: 0;
        margin: 0;
        ```
-   属性简写    
    属性简写需要你非常清楚属性值的**正确顺序**，而且在大多数情况下并不需要设置属性简写中包含的所有值，但是也要视情况而定，如`borde、font`最好是简写，而`margin`等属性，就可以**按需书写**；
-   属性格式
    -   为了保证一致性和可扩展性，每个声明应该用分号结束，每个声明换行。    
    -   属性名的冒号后使用一个空格。出于一致性的原因，属性和值（但属性和冒号之间没有空格）的之间始终使用一个空格。
    -   每个选择器和属性声明总是使用新的一行。
    -   属性选择器或属性值用双引号（””），而不是单引号（”）括起来。
    -   URI值（url()）不要使用引号。
-   选择器使用  
    -   ID的权重过高，**避免使用ID**来解决样式问题
    -   使用子选择器，使用子选择器可以在一定情况下提升性能，避免DOM匹配过多的选择器
        ```
        //bad
        .content .title {
            font-size: 2rem;
        }
        //good
        .content>.title {
            font-size: 2rem;
        }
        ```
    -   选择器中**避免使用标签名**
        ```
            //bad
            div .main{
                color:  #fff
            }
            //good
            .main{
                color:  #fff
            }
        ```
    -   **避免使用important**，尽量从源头去改样式，而不是一刀切的去处理
## JS规范
-   书写规范（**可以使用JS格式化插件**）
    -   缩进使用soft tab（4个空格）。
    -   单行长度不要超过80，但如果编辑器开启word wrap可以不考虑单行长度。
    -   **更多JS优化书写查看**[参考目录](#参考目录)
## 编辑器插件
-   vscode
    -   代码格式化插件 
        -   JS-CSS-HTML formatter  
        -   beautify【IDE】/prettier【Pro】
        -   vue-beautify
        -   CSS Formatter
    -   代码规范检查插件
        -   HTMLHint
        -   StyleLint/CSSHint
        -   ESLint/HTMLCS
    -   标签自动补全插件
        -   auto rename tag
    -   本地服务器
        -   Preview on Web Server
    -   生成注释
        -   Document This （**只支持JS文件**）
    -   局部立即执行
        -   Code Runner
## 参考目录：
[前端开发规范【原生+Vue】_v190221](http://note.youdao.com/noteshare?id=92a6ce460f3d3501c1e1478359eaec14)    
[Code Guide by @AlloyTeam](http://alloyteam.github.io/CodeGuide/#js-variable-declaration)   
[前端开发规范：命名规范、html规范、css规范、js规范](https://juejin.im/post/592d4a5b0ce463006b43b6da)      
[书写具备一致风格、通俗易懂 JavaScript 的原则](https://github.com/rwaldron/idiomatic.js/tree/master/translations/zh_CN)     
[Web前端开发标准规范总结](https://yq.aliyun.com/articles/630735)

