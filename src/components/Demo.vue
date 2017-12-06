<template>
  <div class="demo">
    <div class="title">
      TYTimeLine
    </div>
    <div class="tip">
      1. 基于vue封装的时间线列表组件 <br>
      2. 点击图片，子组件会传出图片的url
    </div>
    <ty-time-line
    v-for="(item, index) in timeList"
    :key="index"
    :isFirst="index === 0 ? true : false"
    :date="item.time"
    :name="item.name"
    :duration="item.duration"
    :hasSpecial="item.hasSpecial"
    :tools="item.tools"
    :description="item.description"
    :imgs="item.imgs"
    @clickImg="showBigImg"
    ></ty-time-line>
  </div>
</template>

<script>
import TYTimeLine from './TYTimeLine'
export default {
  name: 'Demo',
  data () {
    return {
      timeList: [
        {
          time: '2017-1-1',
          name: '博士',
          duration: '一年',
          hasSpecial: '没有',
          tools: '科研，科研，科研',
          description: '博士是标志一个人具备出原创成果的能力或学力的学位，是目前最高级别的学位。拥有博士学位或博士学位同等学力，意味着一个人有能力由学习阶段进入学术阶段。具备出原创成果的能力或学力是博士学位的核心内涵，也是拥有博士学位的人的最本质特征。',
          imgs: ['http://img3.imgtn.bdimg.com/it/u=49266930,647520525&fm=27&gp=0.jpg', 'http://img3.imgtn.bdimg.com/it/u=323882547,4029653554&fm=200&gp=0.jpg', 'http://img5.imgtn.bdimg.com/it/u=3506428747,448563976&fm=200&gp=0.jpg']
        },
        {
          time: '2016-1-1',
          name: '硕士',
          duration: '一年',
          hasSpecial: '没有',
          tools: '研究，研究，研究',
          description: '硕士是标志一个人具备出原创成果的能力或学力的学位，是目前最高级别的学位。拥有博士学位或博士学位同等学力，意味着一个人有能力由学习阶段进入学术阶段。具备出原创成果的能力或学力是博士学位的核心内涵，也是拥有博士学位的人的最本质特征。',
          imgs: ['http://img0.imgtn.bdimg.com/it/u=127133090,329125972&fm=11&gp=0.jpg', 'http://img3.imgtn.bdimg.com/it/u=323882547,4029653554&fm=200&gp=0.jpg', 'http://a.hiphotos.baidu.com/image/pic/item/3c6d55fbb2fb4316c594ca942aa4462308f7d351.jpg']
        },
        {
          time: '2015-1-1',
          name: '学士',
          duration: '一年',
          hasSpecial: '没有',
          tools: '学习，学习，学习',
          description: '学士是标志一个人具备出原创成果的能力或学力的学位，是目前最高级别的学位。拥有博士学位或博士学位同等学力，意味着一个人有能力由学习阶段进入学术阶段。具备出原创成果的能力或学力是博士学位的核心内涵，也是拥有博士学位的人的最本质特征。',
          imgs: ['http://img0.imgtn.bdimg.com/it/u=127133090,329125972&fm=11&gp=0.jpg', 'http://img3.imgtn.bdimg.com/it/u=323882547,4029653554&fm=200&gp=0.jpg', 'http://a.hiphotos.baidu.com/image/pic/item/3c6d55fbb2fb4316c594ca942aa4462308f7d351.jpg']
        },
        {
          time: '2014-1-1',
          name: '高中',
          duration: '一年',
          hasSpecial: '没有',
          tools: '高考，高考，高考',
          description: '高中是标志一个人具备出原创成果的能力或学力的学位，是目前最高级别的学位。拥有博士学位或博士学位同等学力，意味着一个人有能力由学习阶段进入学术阶段。具备出原创成果的能力或学力是博士学位的核心内涵，也是拥有博士学位的人的最本质特征。',
          imgs: ['http://img0.imgtn.bdimg.com/it/u=127133090,329125972&fm=11&gp=0.jpg', 'http://img3.imgtn.bdimg.com/it/u=323882547,4029653554&fm=200&gp=0.jpg', 'http://a.hiphotos.baidu.com/image/pic/item/3c6d55fbb2fb4316c594ca942aa4462308f7d351.jpg']
        }
      ]
    }
  },
  components: {
    'ty-time-line': TYTimeLine
  },
  methods: {
    showBigImg: function (src, srcs) {
      console.debug('我是大图：' + src)
    }
  },
  mounted: function () {
    document.getElementsByTagName('body')[0].style.backgroundColor = '#f2f2f2'
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title {
  font-size: 20px;
  font-weight: bold;
  height: 30px;
  line-height: 30px;
  background-color: rgb(215, 215, 215);
}
.tip {
  text-align: left;
  background-color: rgb(215, 215, 215);
}
</style>
