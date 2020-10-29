# cloudmusic
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

