<template>
  <el-card>
    <h1 class="me-author-name">芝码小咚</h1>
    <div class="image">
      <img src="/static/user/img_1.png" width=100% height=auto>
    </div>
    <div class="me-author-description" align="center">
      <span><i class="el-icon-location-outline"></i> &nbsp;北京</span>&nbsp;&nbsp;&nbsp;&nbsp;
      <span><i class="me-icon-job"></i> &nbsp;java学徒</span>
    </div>
    <!--彩色滚动字体-->
    <div id="rollText" class="m-margin-top"></div>
    <div class="me-author-tool">
      <i @click="showTool(qq)" :title="qq.title" class="iconfont icon-qq"></i>
<!--      <i @click="showTool(bilibili)" :title="bilibili.title" class="iconfont icon-bilibili-fill"></i>-->
      <i @click="showTool(github)" :title="github.title" >
        <svg style="height: 30px;width: 30px" t="1653840496360" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="4025" width="200" height="200">
          <path d="M512 85.333333C276.266667 85.333333 85.333333 276.266667 85.333333 512a426.410667 426.410667 0 0 0 291.754667 404.821333c21.333333 3.712 29.312-9.088 29.312-20.309333 0-10.112-0.554667-43.690667-0.554667-79.445333-107.178667 19.754667-134.912-26.112-143.445333-50.133334-4.821333-12.288-25.6-50.133333-43.733333-60.288-14.933333-7.978667-36.266667-27.733333-0.554667-28.245333 33.621333-0.554667 57.6 30.933333 65.621333 43.733333 38.4 64.512 99.754667 46.378667 124.245334 35.2 3.754667-27.733333 14.933333-46.378667 27.221333-57.045333-94.933333-10.666667-194.133333-47.488-194.133333-210.688 0-46.421333 16.512-84.778667 43.733333-114.688-4.266667-10.666667-19.2-54.4 4.266667-113.066667 0 0 35.712-11.178667 117.333333 43.776a395.946667 395.946667 0 0 1 106.666667-14.421333c36.266667 0 72.533333 4.778667 106.666666 14.378667 81.578667-55.466667 117.333333-43.690667 117.333334-43.690667 23.466667 58.666667 8.533333 102.4 4.266666 113.066667 27.178667 29.866667 43.733333 67.712 43.733334 114.645333 0 163.754667-99.712 200.021333-194.645334 210.688 15.445333 13.312 28.8 38.912 28.8 78.933333 0 57.045333-0.554667 102.912-0.554666 117.333334 0 11.178667 8.021333 24.490667 29.354666 20.224A427.349333 427.349333 0 0 0 938.666667 512c0-235.733333-190.933333-426.666667-426.666667-426.666667z" fill="#000000" p-id="4026"></path>
        </svg>
      </i>
    </div>
  </el-card>

</template>

<script>
  export default {
    name: 'CardMe',
    data() {
      return {
        qq: {title: 'QQ', message: '2434877135'},
        bilibili: {
          title: '哔哩哔哩',
          message: '<a target="_blank" href="https://space.bilibili.com/473844125">https://space.bilibili.com/473844125</a>'
        },
        github: {
          title: 'github',
          message: '<a target="_blank" href="https://github.com/fieldf">https://github.com/fieldf</a>'
        }
      }
    },
    watch: {
      'introduction.rollText'() {
        // if (this.introduction.rollText.length != 0) {
        if (true) {
          //等待 id="rollText"的div加载完毕
          this.$nextTick(() => {
            this.rollText()
          })
        }
      }
    },
    methods: {
      rollText() {
        let r = document.getElementById('rollText')
        let l = ""
        let o = "上海一上来就打开数据连锁酒店".map(function (r) {
          return r + ""
        })
        let a = 2
        let g = 1
        let s = 5
        let d = 75
        let b = ["rgb(110,64,170)", "rgb(150,61,179)", "rgb(191,60,175)", "rgb(228,65,157)", "rgb(254,75,131)", "rgb(255,94,99)", "rgb(255,120,71)", "rgb(251,150,51)", "rgb(226,183,47)", "rgb(198,214,60)", "rgb(175,240,91)", "rgb(127,246,88)", "rgb(82,246,103)", "rgb(48,239,130)", "rgb(29,223,163)", "rgb(26,199,194)", "rgb(35,171,216)", "rgb(54,140,225)", "rgb(76,110,219)", "rgb(96,84,200)"]
        let c = {text: "", prefixP: -s, skillI: 0, skillP: 0, direction: "forward", delay: a, step: g}

        function t() {
          return b[Math.floor(Math.random() * b.length)]
        }

        function e() {
          return String.fromCharCode(94 * Math.random() + 33)
        }

        function n(r) {
          for (var n = document.createDocumentFragment(), i = 0; r > i; i++) {
            let l = document.createElement("span")
            l.textContent = e(), l.style.color = t(), n.appendChild(l)
          }
          return n
        }

        function i() {
          let t = o[c.skillI]
          c.step ? c.step-- : (c.step = g, c.prefixP < l.length ? (c.prefixP >= 0 && (c.text += l[c.prefixP]), c.prefixP++) : "forward" === c.direction ? c.skillP < t.length ? (c.text += t[c.skillP], c.skillP++) : c.delay ? c.delay-- : (c.direction = "backward", c.delay = a) : c.skillP > 0 ? (c.text = c.text.slice(0, -1), c.skillP--) : (c.skillI = (c.skillI + 1) % o.length, c.direction = "forward")), r.textContent = c.text, r.appendChild(n(c.prefixP < l.length ? Math.min(s, s + c.prefixP) : Math.min(s, t.length - c.skillP))), setTimeout(i, d)
        }

        i()
      },
      showTool(tool) {
        this.$message({
          duration: 0,
          showClose: true,
          dangerouslyUseHTMLString: true,
          message: '<strong>' + tool.message + '</strong>'
        });
      }
    }
  }
</script>

<style scoped>
  .me-author-name {
    text-align: center;
    font-size: 30px;
    border-bottom: 1px solid #5FB878;
  }

  .me-author-description {
    padding: 8px 0;
  }

  .me-icon-job {
    padding-left: 16px;
  }

  .me-author-tool {
    text-align: center;
    padding-top: 10px;
  }

  .me-author-tool i {
    cursor: pointer;
    padding: 4px 10px;
    font-size: 30px;
  }
</style>
