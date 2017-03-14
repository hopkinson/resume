<template>
  <div id="app">
    <StyleEditor ref="styleEditor" :code="currentStyle"></StyleEditor>
    <ResumeEditor ref="resumeEditor" :markdown="currentMarkdown" :enableHtml="enableHtml"></ResumeEditor>
  </div>
</template>

<script>
  import StyleEditor from './components/StyleEditor'
  import ResumeEditor from './components/ResumeEditor'
  import './assets/reset.css'

  export default {
    name: 'app',
    components: {
      StyleEditor,
      ResumeEditor
    },
    data() {
      return {
        interval: 50,
        currentStyle: '',
        enableHtml: false,
        fullStyle: [
          `/*
* 大家好，我是何志成（JasonHo）
* live in 天河区
* 这是我的简历！
* 我是一名FE，前端工程师！（1年工作经验）
* 我的联系方式是：1651690426@qq.com

*/

/* 首先给所有元素加上过渡效果 */
* {
  -webkit-transition: all .3s;
  transition: all .3s;
}
/* 白色背景太单调了，我们来点背景 */
html {
  color: rgb(222,222,222); background: rgb(0,43,54); 
}
/* 文字离边框太近了 */
.styleEditor {
  padding: .5em;
  border: 1px solid;
  margin: .5em;
  overflow: auto;
  width: 45vw; height: 90vh;
}
/* 代码高亮 */
.token.selector{ color: rgb(133,153,0); }
.token.property{ color: rgb(187,137,0); }
.token.punctuation{ color: yellow; }
.token.function{ color: rgb(42,161,152); }

/* 加点 3D 效果呗 */
html{
  -webkit-perspective: 1000px;
          perspective: 1000px;
}
.styleEditor {
  position: fixed; left: 0; top: 0; 
  -webkit-transition: none; 
  transition: none;
  -webkit-transform: rotateY(10deg) translateZ(-100px) ;
          transform: rotateY(10deg) translateZ(-100px) ;
}

/* 接下来我给自己准备一个编辑器 */
.resumeEditor{
  position: fixed; right: 0; top: 0;
  padding: .5em;  margin: .5em;
  width: 48vw; height: 90vh; 
  border: 1px solid;
  background: white; color: #222;
  overflow: auto;
}
/* 好了，我开始写简历了 */


`,
          `
/* 这个简历好像差点什么
 * 对了，这是 Markdown 格式的，我需要变成对 HR 更友好的格式
 * 简单，用开源工具翻译成 HTML 就行了
 */
`
          ,
          `
/* 再对 HTML 加点样式 */
.resumeEditor{
  padding: 2em;
}
.resumeEditor h2{
  display: inline-block;
  border-bottom: 1px solid;
  margin: 1em 0 .5em;
}
.resumeEditor ul,.resumeEditor ol{
  list-style: none;
}
.resumeEditor ul> li::before{
  content: '•';
  margin-right: .5em;
}
.resumeEditor ol {
  counter-reset: section;
}
.resumeEditor ol li::before {
  counter-increment: section;            
  content: counters(section, ".") " ";  
  margin-right: .5em;
}
.resumeEditor blockquote {
  margin: 1em;
  padding: .5em;
  background: #ddd;
}
`],
        currentMarkdown: '',
        fullMarkdown: `何志成
----

技能
----

* 前端开发
* Vue2.js 开发
* Node.js 开发

工作经历
----

1. 广州和元达信息科技有限公司
2. 广州鼎梵数码科技有限公司
3. 中国科学院沈阳自动化研究所广州分所

证书
----
大学英语六级

最新项目
----
佛山安信证券微信企业号和PC端管理系统的开发

项目描述：
1.该项目主要是为了解决证券营业部里的理财经理和投资顾问通过“打电话发短信”等方法，
给客户等工作效率低下和成本高的问题，
开发该系统可以通过微信企业号的方式来打通员工和客户沟通难或者客户及时收到资讯。
2.该项目的PC端和移动端的系统两者都采用了Vue.js（版本为2.0）+Webpack等主流框架搭建，
当中还结合了七牛云存储实现CDN的内容存储。
3.与3个后台人员进行沟通接口的数据结构以及部分数据字典。
4.与产品经理进行页面交互设计的讨论，以及原型图的设计。

责任描述：
在本项目中本人主要是作为前端Leader的角色统筹整个项目，
因为该项目团队只有我一个人是前端，
独立完成了整个项目的前端开发和产品页面设计工作，
初期前端框架技术选型、搭建与维护，开发之前编写前端开发规范文档，
开发中自己把握进度，2个月的时间按时完成交付，还受到佛山总部高管的赞扬。

链接：
  移动端 http://1.tviapi.g-easy.com.cn （账号：15625554062，密码：000000）
  PC端 http://admin.tviapi.g-easy.com.cn/#/login （账号：admin，密码：1）

自我评价
----
能够编写语义化的 HTML ，
模块化的 CSS ，
完成较复杂的布局，
熟悉已标准化的 HTML5 / CSS3 新特性，
做到响应式布局和各主流浏览器适配，在项目中运用CSS 动态语言 Sass 。
熟悉原生 Javascript 在项目中运用Vue.js和Angular.js等主流框架，
此外，还喜欢参与研究产品用户体验与交互。有较强的独立工作能力和良好的团队合作精神；
在以前的工作中积累了一定的工作经验及技巧 ,
在公司负责前端框架技术选型、搭建与维护，
Web前端前端多终端的整体前端开发，前端开发规范。
除了集体项目之外，还做了一些个人外包项目。
　　性格随和乐观，积极向上，爱好广泛，喜欢钻研，工作认真负责，
拥有较强的组织能力和适应能力，并具有良好的身体素质。
乐于沟通，易于融入集体，乐于助人，学习能力较好，注重理论与实践相结合，
在工作中不断提高专业知识之余，同时也在不断地提高做人、做事的的能力，
争取将工作做得更好，争取做更好的自己。

GITHUB
----
* [GitHub](https://github.com/hopkinson)
`
      }
    },
    created() {
      this.makeResume()
    },

    methods: {
      makeResume: async function () {
        await this.progressivelyShowStyle(0)
        await this.progressivelyShowResume()
        await this.progressivelyShowStyle(1)
        await this.showHtml()
        await this.progressivelyShowStyle(2)
      },
      showHtml: function () {
        return new Promise((resolve, reject) => {
          this.enableHtml = true
          resolve()
        })
      },
      progressivelyShowStyle(n) {
        return new Promise((resolve, reject) => {
          let interval = this.interval
          let showStyle = (async function () {
            let style = this.fullStyle[n]
            if (!style) { return }
            // 计算前 n 个 style 的字符总数
            let length = this.fullStyle.filter((_, index) => index <= n).map((item) => item.length).reduce((p, c) => p + c, 0)
            let prefixLength = length - style.length
            if (this.currentStyle.length < length) {
              let l = this.currentStyle.length - prefixLength
              let char = style.substring(l, l + 1) || ' '
              this.currentStyle += char
              if (style.substring(l - 1, l) === '\n' && this.$refs.styleEditor) {
                this.$nextTick(() => {
                  this.$refs.styleEditor.goBottom()
                })
              }
              setTimeout(showStyle, interval)
            } else {
              resolve()
            }
          }).bind(this)
          showStyle()
        })
      },
      progressivelyShowResume() {
        return new Promise((resolve, reject) => {
          let length = this.fullMarkdown.length
          let interval = this.interval
          let showResume = () => {
            if (this.currentMarkdown.length < length) {
              this.currentMarkdown = this.fullMarkdown.substring(0, this.currentMarkdown.length + 1)
              let lastChar = this.currentMarkdown[this.currentMarkdown.length - 1]
              let prevChar = this.currentMarkdown[this.currentMarkdown.length - 2]
              console.log(prevChar)
              if (prevChar === '\n' && this.$refs.resumeEditor) {
                this.$nextTick(() => this.$refs.resumeEditor.goBottom())
              }
              setTimeout(showResume, interval)
            } else {
              resolve()
            }
          }
          showResume()
        })
      }
    }
  }

</script>

<style scoped>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  
  html {
    min-height: 100vh;
  }
  
  * {
    -webkit-transition: all .3s;
    transition: all .3s;
  }
</style>
