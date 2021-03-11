<template>
  <block-wrapper
    id="project"
    title="项目经验"
    theme="dark"
  >
    <template v-for="(project, pIndex) in projects">
      <block-wrapper
        v-if="project.secondPage"
        id="second-page-title"
        :key="`${pIndex}-page-title`"
        title="项目经验"
        theme="dark"
      >
        <p class="project-company seconde-page-company">
          {{ project.company }}
        </p>
      </block-wrapper>
      <p
        v-if="project.company && !project.secondPage"
        :key="`company-${pIndex}`"
        class="project-company"
      >
        {{ project.company }}
      </p>
      <text-section
        :key="`project${pIndex}`"
        :title="project.title"
      >
        <template slot="title">
          <flex
            justify="space-between"
            align="center"
            wrap="wrap"
          >
            <div class="project-header">
              <h1 class="project-title">
                {{ project.title }}
              </h1>
              <span
                v-if="project.time"
                class="project-time"
              >
                {{ project.time.start }} - {{ project.time.end }}
              </span>
            </div>
            <div
              v-if="project.tags && project.tags.length > 0"
              class="project-tag-wrapper"
            >
              <div
                v-for="(tag, tagIndex) in project.tags"
                :key="`${pIndex}-tag${tagIndex}`"
                class="project-tag"
              >
                {{ tag }}
              </div>
            </div>
          </flex>
        </template>
        <p>
          <span class="title">
            主要技术栈:
          </span>
          <template v-for="(tech, techIndex) in project.techs">
            <em :key="`${pIndex}-tech-${techIndex}`">
              {{ tech }}
            </em>
            {{ !isLastOf(project.techs, techIndex) ? "、" : "" }}
          </template>
        </p>
        <p>
          <span class="title">
            项目描述:
          </span>
          <template v-for="(feature, fIndex) in project.features">
            <span :key="`${fIndex}-duty${fIndex}`">
              <span v-html="feature" />
              {{ !isLastOf(project.features, fIndex) ? "；" : "" }}
            </span>
          </template>
        </p>

        <p class="title">
          项目职责: <strong :style="{color: '#666'}">
            {{ project.role }}
          </strong>
        </p>
        <ul>
          <li
            v-for="(duty, dIndex) in project.dutys"
            :key="`${pIndex}-row-${dIndex}}`"
            v-html="duty"
          />
        </ul>
      </text-section>
      <flex
        v-if="pIndex === 2"
        :key="`more${pIndex}`"
        class="more"
        justify="center"
        direction="column"
        align="center"
      >
        <span class="more-text">
          More
        </span>
        <i class="el-icon-caret-bottom more-icon" />
      </flex>
    </template>
  </block-wrapper>
</template>

<script>
import { BlockWrapper, TextSection, Flex } from '@/components';

export default {
  name: 'Project',
  components: {
    BlockWrapper,
    TextSection,
    Flex,
  },
  data() {
    return {
      projects: [
        {
          company: '华强方特文化科技集团股份有限公司 - 项目',
          title: '采云团购',
          role: '前端开发、后端开发',
          time: {
            start: '2020.4',
            end: '至今',
          },
          techs: ['VueJs', 'Vuex', 'ElementUI', 'axios', 'VantUI', 'Asp.Net Core', 'Abp vNext'],
          features: [
            '帮助集团实现电商式采购，人人都是采购员，针对集团多种采购模式定制化开发，逐步替代用友NC系统',
            '产品模块包括基础数据、物料申领申购、供应商询报价及管理、合同/订单生成、库存管理。',
          ],
          dutys: [
            '独立完成基于<em>VueJs</em>、<em>ElementUI</em>管理后台系统的开发',
            '基于<em>vue-pdf</em>、<em>pdf.js</em></em>、<em>html2canvas</em>封装组件, 实现合同、订单预览打印',
            '基于<em>ElementUI</em>封装可复用组件库</em>',
            '使用<em>VantUI</em>开发嵌入集团秒通App单据信息进行数据可视化展示',
            '基于<em>Asp.Net Core</em>、<em>Abp vNext</em>框架完成接口开发',
            '系统日常迭代开发、维护及优化',
          ],
          tags: ['采购报价平台'],
        },
        {
          title: '方特旅游WebApp',
          time: {
            start: '2017.8',
            end: '2018.9',
          },
          role: '前端开发、后端开发',
          techs: ['MVC', 'JQuery', 'Asp.Net Core'],
          features: [
            '通过与集团各平台打通, 整合公园门票预订、停车缴费、酒店预订等订单信息供游客使用',
          ],
          dutys: [
            '负责门票、停车缴费等页面开发',
            '通过与后台接口联动，并使用百度地图API定位公园及停车场信息',
            '负责Wap端的项目重构、集团其他系统接口对接、项目搭建架构及开发工作',
          ],
          tags: ['旅游购票'],
        },
        {
          title: '方特集市小程序',
          time: {
            start: '2018.1',
            end: '2018.7',
          },
          role: '小程序开发、后台开发、接口开发',
          techs: ['Wechat Mini Program', 'VueJs', 'ElementUI', 'axios', 'Asp.Net Core', 'Abp'],
          dutys: [
            '集团内部二手闲置发布，租房信息共享或转租，周边消费优惠信息',
            '使用<em>ElementUI</em>开发后台管理系统，并使用<em>vue-i18n</em>实现多国语言切换功能',
            '完成微信小程序内部搜索、二手/租房信息展示等功能开发',
            '使用<em>Abp</em>、<em>Asp.Net Core</em>实现后台接口开发',
          ],
          features: [
            '集团内部员工租房信息、二手信息、集团周边优惠、及社团信息展示',
            '服务于全国各地公园城市',
          ],
          tags: ['微信小程序'],
        },
        {
          title: '方特图库',
          time: {
            start: '2018.1',
            end: '2018.7',
          },
          role: '前端开发、接口开发',
          techs: ['VueJs', 'iViewUI', 'axios', 'Asp.Net Core', 'Abp vNext'],
          dutys: [
            '使用<em>iViewUI</em>完成PC端后台管理的开发',
            '使用<em>Abp vNext</em>搭建系统框架',
            '使用<em>Abp vNext</em>、<em>Asp.Net Core</em>实现后台接口开发',
          ],
          features: [
            '集团内部设计素材、版权内容管理、文章/创作分享平台',
          ],
          tags: ['图文平台'],
        },
        {
          title: '方特酒店预订系统',
          time: {
            start: '2018.1',
            end: '2018.7',
          },
          role: '后端开发',
          techs: ['VueJs', 'ElementUI', 'axios', 'Asp.Net Core', 'Abp'],
          dutys: [
            '基于<em>Abp</em>框架搭建系统，并对接集团内部票务、订单中心、支付等系统',
            '对接<em>千里马</em>系统，定制各酒店房源信息',
            '使用<em>ElementUI</em>开发后台管理系统，并使用<em>vue-i18n</em>实现多国语言切换功能',
          ],
          features: [
            '基于千里马系统定制化开发的酒店预订系统，可集成到集团各销售平台，拥有属于自己的房源信息管理就订单信息',
            '支持支付宝、微信等多种支付方式, 服务于集团旗下酒店, 并成功帮助商户提高业绩',
          ],
          tags: ['酒店预订'],
        },

        {
          company: '重庆杰特科技发展有限公司 - 项目',
          title: '旺点美容美发管理软件',
          time: {
            start: '2018.11',
            end: '2020.2',
          },
          role: '维护迭代',
          techs: ['.Net', 'Winform'],
          dutys: [
            '负责迭代更新及维护Winform版本软件的开发',
            '多处使用多线程及自定义控件、组件的方式',
          ],
          features: [
            '集收银、经销存、会员管理、内容管理一体的管理系统',
            '用于大型连锁店铺管理',
          ],
          tags: ['美容美发行业软件'],
        },
        {
          title: '旺点手机收银',
          role: '前端开发',
          time: {
            start: '2019.5',
            end: '2020.1',
          },
          tags: ['Hybrid App'],
          techs: ['.Net', 'Mvc', 'Hybrid'],
          dutys: [
            '基于<em>.Net</em>Mvc框架开发的嵌入式<em>Hybrid</em>移动App',
            '基于<em>Hybrid</em>实现扫码，Wifi等App原生特性',
          ],
          features: [
            '基于Hybrid开发的App可以原生App的部分功能，达到快速且高效的开发速度',
          ],
        },
      ],
    };
  },
  methods: {
    isLastOf(list, index) {
      const { length } = list;
      return index === length - 1;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../../styles/common.scss";
ul {
  margin: 0;
  padding-left: 5px;
  text-align: left;
}
ul li {
  list-style: none;
  line-height: 1.8;
  &:before {
    content: "●"; //'\25CF'
    margin-right: 5px;
    color: $deep-blue;
    display: inline-block;
  }
}
#second-page-title{
  display: none;
}
.more {
  color: $deep-blue;
  &-text,
  &-icon {
    display: none;
    font-weight: bold;
    font-size: 18px;
  }
}
.title {
  color: $deep-blue;
  font-weight: bold;
}
.project-company {
  // margin-top: 10px;
  text-align: center;
  color: #333;
  font-weight: bold;
}
.project-header {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  .project-title {
    margin-right: 10px;
  }
  .project-time {
    font-size: 16px;
    color: #666;
    font-weight: bold;
  }
}
.project-tag-wrapper {
  display: flex;
  flex-shrink: 0;
  .project-tag {
    margin: 10px 5px;
    background: #cfffd9;
    color: $deep-blue;
    padding: 0 15px;
    line-height: 2;
    border-radius: 15px;
    font-weight: bold;
    &:first-child {
      margin-left: 0;
    }
  }
}
</style>
