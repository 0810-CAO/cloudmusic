# cloudmusic
# 1.单页Web应用（SPA - Single Page web Application）
也就是说只有一个HTML文件的Web应用, 我们就称之为单页Web应用, 就称之为SPA应用
我们通过Vue开发的项目其实就是典型的SPA应用
# 2.SPA的特点:
1) SPA应用只有一个HTML文件, 所有的内容其实都在这个页面中呈现的
2) SPA应用只会加载一次HTML文件, 不会因为用户的操作而进行页面的重新加载
当用户与应用程序交互时, 是通过动态更新页面内容的方式来呈现不同的内容
# 3. SPA优点:
1) 有良好的交互体验
不会重新加载整个网页, 只是局部更新
2) 前后端分离开发
前端负责页面呈现和交互, 后端负责数据
3) 减轻服务器压力
只用处理数据不用处理界面
4) 共用一套后端程序代码
# 4. SPA缺点：
1) SEO难度较高
只有一个界面, 无法针对不同的内容编写不同的SEO信息
2) 初次加载耗时多
为实现单页Web应用功能及显示效果，需要在加载页面的时候将所有JavaScript、CSS统一加载，
在Vue中可以使用按需加载解决
# 1.如何解决单页面应用的SEO困难问题?
解决这个问题之前首先我们需要了解常见的三种网页渲染方式
## 1.1客户端渲染(CSR  - Client Side Render)
后端只提供数据，前端做视图和交互逻辑(SPA应用就是典型的客户端渲染)
### 1.2客户端渲染过程
1. 客户端请求html (请求)
2. 服务端返回html
3. 客户端渲染HTML,找到依赖的JS/CSS文件
3. 客户端请求对应的JS/CSS文件 (请求)
4. 服务端返回对应的JS/CSS文件
5. 客户端等待JS/CSS文件下载完成
6. 客户端加载并初始化下载好的JS文件
7. 客户端执行JS代码向后端请求数据 (请求)
8. 服务端返回数据
9. 客户端利用服务端返回的数据填充网页
最大优点: 交互体验好可以做局部更新
最大缺点: 首屏加载慢(因为要等到HTML下载完才会去下载JS/CSS, 要等到JS下载完初始化完才会去获取数据),
## 1.2服务端渲染(SSR - Server Side Render)
后端既提供数据又提供视图和交互逻辑
也就是服务器接到客户端请求之后，找到对应的数据并根据找到的数据生成对应的视图
然后将包含数据的视图一次性发给客户端，客户端直接将渲染即可
### 1.2服务端渲染过程
1.客户端请求html (请求)
2.服务端内部查找对应的html文件和数据
3.服务器内部根据数据html文件和数据生成完整网页
4.服务端返回完整网页
5.客户端渲染HTML,找到依赖的JS/CSS文件
5.客户端请求对应的JS/CSS文件 (请求)
6.客户端等待JS/CSS文件下载完成
7.客户直接展示网页
最大优点: 首屏加载快(因为服务器返回的网页已经包含数据, 所以之下载完JS/CSS就可以直接渲染)
          每次请求返回的都是一个独立完成的网页, 更利于SEO
最大缺点:网络传输数据量大
## 1.3预渲染
无需服务器实时动态编译，采用预渲染，在构建时针对特定路由简单的生成静态HTML文件
本质就是客户端渲染, 只不过和SPA不同的是预渲染有多个界面
最大优点: 由于有多个界面, 所以更利于SEO
最大缺点: 首屏加载慢, 预编译会非常的慢
## 1.4如何选择
1.注重SEO的新闻、电商网站，建议采用服务器端渲染
2.强交互的页面，不注重SEO，采用客户端渲染
3.两者之间, 只需改善少数页面的SEO，采用预渲染
# 1.使用预渲染解决SPA应用SEO问题
https://www.npmjs.com/package/vue-cli-plugin-prerender-spa
注意点: Router必须使用history模式
# 2.使用vue-meta-info统一管理SEO三大标签
https://www.npmjs.com/package/vue-meta-info

```
.
├── README.md			
├── babel.config.js			
├── dist                                打包文件         									   
├── package-lock.json                   包下载版本管理
├── package.json                        包依赖管理           
├── postcss.config.js                   px转换为rem
├── public                              
│   ├── apple-touch-icon.png            苹果的私有属性
│   ├── apple-touch-icon114.png         苹果的私有属性114*114
│   ├── apple-touch-icon152.png         苹果的私有属性152*152
│   ├── apple-touch-icon180.png         苹果的私有属性180*180
│   ├── favicon.ico                     网页logo
│   └── index.html                      首页
├── src
│   ├── App.vue                         主组件
│   ├── api
│   │   ├── dist
│   │   │   ├── index.dev.js
│   │   │   └── network.dev.js
│   │   ├── index.js                    请求接口方法
│   │   └── network.js                  封装axios方法及拦截器
│   ├── assets
│   │   ├── css                         css文件
│   │   │   ├── base.scss               html/body/img格式化文件
│   │   │   ├── dist
│   │   │   ├── mixin.scss              移动端不同像素界面文字图片大小、限制行数、不换行、背景切换方法
│   │   │   ├── reset.scss              整体的格式化文件
│   │   │   └── variable.scss           移动端字体颜色/大小、背景色
│   │   └── images                      不同尺寸提供的图片
│   │ 
│   ├── components
│   │   ├── Account
│   │   │   ├── AccountBottom.vue       个人页面底部（歌曲信息）
│   │   │   └── AccountHeader.vue       个人页面顶部（切换收藏、历史歌曲）
│   │   ├── Detail
│   │   │   ├── DetailBottom.vue        详情页底部（歌曲列表）
│   │   │   ├── DetailHeader.vue        详情页顶部（返回上一级、切换背景）        
│   │   │   └── DetailTop.vue           详情页头部（封面图片）           
│   │   ├── Header.vue                  顶部自定义插槽
│   │   ├── MainHeader.vue              首页顶部
│   │   ├── Player
│   │   │   ├── ListPlayer.vue          播放列表
│   │   │   ├── MiniPlayer.vue          迷你播放模块
│   │   │   ├── NormalPlayer.vue        正常播放模块
│   │   │   ├── PlayerBottom.vue        播放底部（收藏、切歌、播放、播放列表显示按钮）
│   │   │   ├── PlayerHeader.vue        播放头部（当前播放歌曲作者、名称）
│   │   │   └── PlayerMiddle.vue        播放中部（歌曲封面、歌词列表 可切换显示）
│   │   ├── Recommend
│   │   │   ├── Banner.vue              推荐页（轮播图）
│   │   │   ├── Personalized.vue        推荐歌单、专辑logo
│   │   │   └── SongList.vue            最新音乐列表
│   │   ├── ScrollView.vue              滚动组件（插槽）
│   │   ├── SongListItem.vue            音乐列表组件（复用）
│   │   └── Tabbar.vue                  顶部导航栏
│   ├── dist
│   │   └── main.dev.js                 开发环境打包入口
│   ├── main.js                         入口文件
│   ├── plugin
│   │   └── loading                     网络请求等待显示插件（拦截器中使用）
│   │       ├── Loading.vue
│   │       ├── dist
│   │       └── index.js
│   ├── router                          路由
│   │   ├── dist
│   │   │   └── index.dev.js
│   │   └── index.js
│   ├── store                           vuex
│   │   ├── actions.js
│   │   ├── getters.js
│   │   ├── index.js
│   │   ├── modeType.js                 播放顺序
│   │   ├── mutations-type.js
│   │   ├── mutations.js
│   │   └── state.js
│   ├── tools                           随机数、格式化时间、持久化方法
│   │   └── tools.js
│   └── views
│       ├── Account.vue                 个人中心
│       ├── Detail.vue                  详情页（首页歌曲/专辑、歌手、排行榜都需要跳转）
│       ├── Player.vue                  播放页
│       ├── Rank.vue                    歌曲榜单页
│       ├── Recommend.vue               推荐页
│       ├── Search.vue                  搜索页
│       └── Singer.vue                  歌手页
├── vue-meta-info.js                    SEO内容
└── vue.config.js                       webpack自定义（预渲染及其优化）
```
