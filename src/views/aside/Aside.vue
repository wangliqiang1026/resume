<template>
  <div class="resume-aside">
    <div class="resume-aside-top">
      <div class="avatar">
        <img src="../../assets/avatar.png">
      </div>

      <div class="personal-desc">
        <p class="name">
          王李强
        </p>
        <p class="position">
          Web前端开发工程师
        </p>
        <p>男 / 1992.11</p>
        <span
          class="work-year"
        >
          6年工作经验
        </span>
      </div>
      <icon-list
        :list="contacts"
        class="icon-list"
      />
      <!-- <div class="online-link">
        <h3>个人博客</h3>
        <a href="https://wangliqiang1026.github.io/">
          https://wangliqiang1026.github.io/
        </a>
      </div> -->
      <block-wrapper
        id="edu"
        title="教育背景"
        class="font-bold"
        theme="dark"
      >
        <div class="text-center">
          <p>西南大学（非统招）</p>
          <p>2011.9 - 2015.7</p>
          <p>计算机及应用 - 本科</p>
        </div>
      </block-wrapper>
      <!-- 技能水平 -->
      <block-wrapper
        id="skill"
        theme="dark"
        title="技能水平"
        class="skill-level"
      >
        <ul>
          <li
            v-for="(skill, skillIndex) in skills"
            :key="`skill${skillIndex}`"
            v-html="skill"
          />
        </ul>
      </block-wrapper>
      <!-- 个人评价 -->
      <block-wrapper
        id="evalution"
        title="个人评价"
        theme="dark"
      >
        <ul>
          <li
            v-for="(comment, commentIndex) in comments"
            :key="`comment${commentIndex}`"
            v-html="comment"
          />
        </ul>
      </block-wrapper>
    </div>


    <div class="resume-aside-bottom" />
  </div>
</template>

<script>
import {
  IconLineList, BlockWrapper,
} from '@/components';


export default {
  name: 'Aside',
  components: {
    'icon-list': IconLineList,
    'block-wrapper': BlockWrapper,
  },
  data() {
    return {
      skills: [
        '具有最新前端技术（面向对象的JavaScript，HTML5，CSS3，VueJS，Bootstrap，jQuery）以及后端技术（.Net Core，Winform，MySQL，Redis）的项目经验',
        '熟悉VueJs框架，可用VueJs进行模块化开发，对ElementUI、vant等前端较熟悉',
        '理解前端工程化, 熟悉项目脚手架及Webpack常用配置; 熟悉git、svn代码协作工具',
        '熟悉前端cookie、localstorage、sessionstorage等存储方式',
      ],
      comments: [
        '拥有长期后端开发经验，对服务端足够了解，熟悉服务端开发流程',
        '拥有公共组件库开发经验, 主导并开发过中大型项目; 拥有自动化部署实践经验',
        '拥有良好的代码编写习惯、清晰的产品思维、良好的业务理解能力、沟通能力和团队协作能力。',
        '较强的自我驱动学习能力, 乐于钻研学习新技术, 时刻关注行业动态拓展视野',
      ],
      contacts: [
        {
          icon: 'email',
          text: 'wangliqiang1026@hotmail.com',
          linkType: 'mailto',
        },
        {
          icon: 'phone',
          text: '18983605769',
          linkType: 'tel',
        },
        // {
        //   icon: 'github',
        //   text: 'https://github.com/wangliqiang1026',
        // },
        {
          icon: 'qq',
          text: '460173373',
        },
      ],

    };
  },
};
</script>

<style lang="scss" scoped>
$bg: #f7f8fa;
@import "../../styles/common.scss";

ul {
  padding-left: 20px;
  li {
    margin-bottom: 5px;
  }
}
.resume-aside {
  position: relative;
  flex: 3;
  display: flex;
  flex-direction: column;
  color: $deep-blue;
  padding: 40px;
  box-sizing: border-box;
  text-align: center;
  background-color: $bg;
  .online-link {
    margin-bottom: 10px;
    h3 {
      margin: 5px 0;
    }

  }
  .icon-list {
    margin-left: 30px;
  }
  .work-year {
    padding: 0 10px;
    display: inline-block;
    background: #E3E6EE;
    color: #333;
    font-size: 15px;
    font-weight: bold;
    border-radius: 10px;
  }
  &-top {
    .avatar {
      width: 220px;
      height: 220px;
      background: #728ce0;
      border-radius: 50%;
      overflow: hidden;
      margin: 0 auto;
      img{
        width: 178.5px;
        height: 220px;
      }
    }
    .personal-desc {
      margin-bottom: 10px;
      .name {
        font-size: 33px;
        // font-weight: bold;
      }
      .position {
        font-size: 18px;
      }
    }
  }
  #blog {
    text-align: center;
    .blog-link {
      font-size: 16px;
      font-weight: bold;
    }
  }

  @media screen and (max-width: 1049px) {
    padding-top: 80px;
    .online-link {
      display: none;
    }
    .icon-list {
      margin-left: calc((100% - 240px) / 2);
    }
  }
}
</style>
