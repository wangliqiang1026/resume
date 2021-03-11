<template>
  <block-wrapper
    id="work"
    title="工作经历"
    theme="dark"
  >
    <div
      v-for="(work, wIndex) in works"
      :key="`work-exp${wIndex}`"
      class="work-exp"
    >
      <p class="work-exp__company">
        {{ work.company }}
      </p>
      <p class="font-bold">
        {{ work.date }}
      </p>
      <p>工作内容：{{ work.duty }}</p>
    </div>
  </block-wrapper>
</template>

<script>
import { BlockWrapper } from '@/components';

export default {
  name: 'Work',
  components: {
    BlockWrapper,
  },
  data() {
    return {
      works: [
        {
          company: '华强方特文化科技集团股份有限公司',
          date: '2018.6 - 至今',
          duty: '独立完成前端开发工作, 主导前端团队公共组件库的封装, 提高团队的开发效率, 负责公司项目的前端、后端开发工作。',
        },
        {
          company: '重庆杰特科技发展有限公司',
          date: '2016.12 - 2018.5',
          duty: '负责公司美容美发行业软件开发，包括移动端Hybrid混合式App（AppCan）、Winform客户端。',
        },

        {
          company: '重庆转购科技有限公司',
          date: '2016.7 - 2016.12',
          duty: '负责公司钱包平台相关项目开发。',
        },
        {
          company: '重庆市亚能软件有限公司',
          date: '2015.3 - 2016.6',
          duty: '负责公司PC端管理后台、微信H5、客户端Winform项目开发。',
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../../../styles/common.scss";

 .work-exp {
    &__company {
      font-size: 16px;
      font-weight: bold;
      color: $deep-blue;

    }
  }
</style>
