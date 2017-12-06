<template>
  <div class="ty-time-line-cell">
    <div class="item-box">
      <div class="item">
        <div class="date-box flex-box">
          <div class="right-box">
            <div class="dot-box">
              <div class="line-box-1">
                <div v-show="!isFirst" class="line-1">
                </div>
              </div>
              <div :class="[isFirst ? 'first-dot' : 'dot']">
              </div>
            </div>
            <div class="line-box-2">
              <div class="line-2">
              </div>
            </div>
          </div>
          <div :class="[isFirst ? 'first-date' : 'date']">
            {{date + (isFirst ? '(最新)' : '')}}
          </div>
        </div>
        <div class="joint-line">
        </div>
        <div class="detail-box">
          <div class="detail">
            <div class="row">
              <span class="row-title">名称：</span>
              {{name}}
            </div>
            <div class="row">
              <span class="row-title">时长：</span>
              {{duration}}
            </div>
            <div class="row">
              <span class="row-title">是否有属性：</span>
              {{hasSpecial}}
            </div>
            <div class="row">
              <span class="row-title">正在使用的工具：</span>
              {{tools}}
            </div>
            <div v-show="showDetail" class="row">
              <span class="row-title">详细描述：</span>
              {{description}}
            </div>
            <div v-show="showDetail" class="row">
              <span class="row-title">详细图片：</span>
            </div>
            <!-- <div v-show="showDetail && imgs.length >= 3" :class="['flex-box':imgs.length >= 3, 'space-around':imgs.length >= 3, 'flex-wrap':imgs.length >= 3]"> -->
            <div v-show="showDetail" :class="imgs.length >= 3 ? ['flex-box','space-around','flex-wrap'] : 'box'">
              <div v-for="(item, index) in imgs" :class="['detail-img-box', {'width-100':imgs.length < 3}]">
                <img :src="item" class="detail-img shrink-none" @click="clickImg(imgs[index], imgs)">
              </div>
            </div>
            <div class="flex-box space-center">
              <div class="shrink-button display-flex-box flex-just-content-center flex-align-items-center" @click="shrink">
                <div class="shrink-button-title">
                  {{shrinkButtonTitle}}
                </div>
                <img :src="shrinkButtonTitle === '展开详情' ? downArrow : upArrow" class="shrink-button-img">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['isFirst', 'date', 'name', 'duration', 'hasSpecial', 'tools', 'description', 'imgs'],
  data () {
    return {
      downArrow: require('../assets/icon_content_n_down.png'),
      upArrow: require('../assets/icon_content_n_up.png'),
      showDetail: false,
      shrinkButtonTitle: '展开详情'
    }
  },
  methods: {
    clickImg: function (src, srcs) { // 点击图片的事件传递
      this.$emit('clickImg', src, srcs)
    },
    shrink: function () { // 收缩列表
      this.showDetail = !this.showDetail
      this.shrinkButtonTitle = this.shrinkButtonTitle === '收起' ? '展开详情' : '收起'
    }
  }
}
</script>

<style scoped>
.ty-time-line-cell {
}
.flex-box {
  display: -webkit-box;
  display: -ms-flexbox;
  display: box;
  display: -webkit-flex;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
        box-orient:horizontal;
          flex-direction: row;
  -webkit-box-align: center;
      -ms-flex-align: center;
      box-align: center;
          align-items: center;
  -webkit-align-items: center;
}
.display-flex-box {
  display: -webkit-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: box;
  display: flex;
}
.flex-align-items-center {
  -webkit-box-align: center;
      -ms-flex-align: center;
      box-align: center;
          align-items: center;
          -webkit-align-items: center;
}
.space-around {
  -webkit-box-pack: justify;
      -ms-flex-pack: justify;
      box-pack: justify;
          justify-content: space-between;
          -webkit-justify-content: space-between
}
.space-center {
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
}
.flex-just-content-center {
  -webkit-box-pack: center;
      -ms-flex-pack: center;
      box-pack: center;
          justify-content: center;
          -webkit-justify-content: center;
}
/*flex设置换行*/
.flex-wrap {
  -ms-flex-wrap: wrap;
      flex-wrap: wrap;
    -webkit-flex-wrap: wrap;
}
/*空间不足的时候不压缩*/
.shrink-none {
  -ms-flex-negative: 0;
  -webkit-flex-shrink: 0;
  -webkit-box-shrink: 0;
      flex-shrink: 0;
}
.item-box {

}
.item {

}
.date-box {
  padding-left: 17px;
}
.date {
  margin-top: 15px;
  padding: 5px 10px;
  color: #999;
  background-color: #e5e5e5;
  border-radius: 5px;
}
.first-date {
  margin-top: 15px;
  padding: 5px 10px;
  color: #fff;
  background-color: #579ff8;
  border-radius: 5px;
}
.right-box {
  height: 43px;
  width: 25px;
}
.dot-box {
  height: 33px;
  width: 25px;
}
.dot {
  width: 11px;
  height: 11px;
  border: solid 1px rgb(204,204,204);
  border-radius: 5.5px;
}
.first-dot {
  width: 11px;
  height: 11px;
  border: solid 1px rgb(135,183,246);
  border-radius: 5px;
}
.line-box-1 {
  width: 25px;
  height: 22px;
  padding-left: 5px;
}
.line-1 {
  width: 1px;
  height: 22px;
  border-left: solid 1px #e5e5e5;
}
.line-box-2 {
  width: 25px;
  height: 10px;
  padding-left: 5px;
}
.line-2 {
  width: 1px;
  height: 10px;
  border-left: solid 1px #e5e5e5;
}
.joint-line {
  margin-left: 22px;
  height: 8px;
  width: 1px;
  border-left: solid 1px #e5e5e5;
}
.detail-box {
  width: 100%;
  background-color: rgb(255,255,255);
  /*background-color: rgb(117, 83, 83);*/
}
.detail {
  margin: 0px 22px;
  padding: 15px 14px;
  border-left: solid 1px #e5e5e5;
}
.row-title {
  font-size: 15px;
  color: #666;
}
.row {
  text-align: left;
  font-size: 15px;
  color: #222;
}
.detail-img-box {
  margin-top: 5px;
  width: 100px;
  /*background-color: rgb(198, 133, 137);*/
}
.width-100 {
  width: 100%;
}
.detail-img {
  max-width: 100%;
  max-height: 100%;
  cursor: pointer;
}
.shrink-button {
  margin-top: 10px;
  width: 100px;
  height: 30px;
  border: solid 1px rgb(231,231,231);
  border-radius: 15px;
  cursor: pointer;
}
.shrink-button-title {
  font-size: 15px;
  color: #12c18f;
}
.shrink-button-img {
  margin-left: 4px;
  width: 9px;
  height: 9px;
}
</style>
