<template>
  <el-card class="me-area" :body-style="{ padding: '16px' }">
    <div class="me-article-header">

      <a @click="view(id)" class="me-article-title">{{title}}</a>
      <el-button v-if="weight > 0" class="me-article-icon" type="info" plain>置顶</el-button>
<!--      <span class="me-pull-right me-article-count">-->
<!--	    	<i class="me-icon-comment"></i>&nbsp;{{commentCounts}}-->
<!--	    </span>-->
      <span class="me-pull-right me-article-count">
	    	<i class="el-icon-view"></i>&nbsp;{{viewCounts}}
	    </span>
    </div>

    <div class="me-artile-description">
      {{summary}}
    </div>
    <div class="me-article-footer">
	  	<span class="me-article-author">
	    	<i class="me-icon-author"></i>&nbsp;{{author}}
	    </span>
      <el-button class="me-article-icon" type="info" plain @click="edit(id)" v-if="user.account=='芝码小咚'">编辑</el-button>
      <el-tag v-for="t in tags" :key="t.tagName" size="mini" style="color: #B500FE;background-color: yellow">{{t.tagName}}</el-tag>

      <span class="me-pull-right me-article-count">
	    	<i class="el-icon-time"></i>&nbsp;{{createDate | format}}
	    </span>

    </div>
  </el-card>
</template>

<script>
  import { formatTime } from "../../utils/time";

  export default {
    name: 'ArticleItem',
    props: {
      id: String,
      weight: Number,
      title: String,
      commentCounts: Number,
      viewCounts: Number,
      summary: String,
      author: String,
      tags: Array,
      createDate: String
    },
    data() {
      return {}
    },
    computed: {
      user() {
        let account = this.$store.state.account
        return {
          account
        }
      }
    },
    methods: {
      view(id) {
        this.$router.push({path: `/view/${id}`})
      },
      edit(id) {
        this.$router.push({path: `/edit/${id}`})
      }
    }
  }
</script>

<style scoped>

  .me-article-header {
    /*padding: 10px 18px;*/
    padding-bottom: 10px;
  }

  .me-article-title {
    font-weight: 600;
  }

  .me-article-icon {
    padding: 3px 8px;
  }

  .me-article-count {
    color: #a6a6a6;
    padding-left: 14px;
    font-size: 13px;
  }

  .me-pull-right {
    float: right;
  }

  .me-artile-description {
    font-size: 13px;
    line-height: 24px;
    margin-bottom: 10px;
  }

  .me-article-author {
    color: #a6a6a6;
    padding-right: 18px;
    font-size: 13px;
  }

  .el-tag {
    margin-left: 6px;
  }

</style>
