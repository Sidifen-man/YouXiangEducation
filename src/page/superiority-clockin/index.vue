<template>
  <div class="g_main">
    <div class="superiority-clockin">
      <div class="superiority-clockin__main">
        <div class="main-header">
          <div class="header-title">
            <img :src="clockInIcon" alt>
            <span>我的优势打卡</span>
          </div>
        </div>
        <div class="main-content">
          <router-view></router-view>
        </div>
      </div>
      <div class="superiority-clockin__asider">
        <div class="asider-header">
          <div class="header-title">
            <img class="plain" :src="myPlain" alt>
          </div>
        </div>
        <div class="asider-main">
          <ul class="activity-list">
            <li
              :class="{'is-active': active === index}"
              @click="handleClick(item,index)"
              class="activity-list-item"
              v-for="(item,index) in activityList"
              :key="index"
            >
              <div class="left">
                <img :src="item.imgSrc" alt>
              </div>
              <div class="right">
                <p class="title">{{item.title}}</p>
                <p class="tip">{{item.tip}}</p>
              </div>
            </li>
          </ul>
          <div class="asider-action">
            <button @click="customActivity">添加自定义活动</button>
            <button>去活动库添加计划</button>
          </div>
        </div>
      </div>
    </div>
    <custom-activity-dialog ref="cuttomActivityDialog"></custom-activity-dialog>
  </div>
</template>
<script>
import clockInIcon from "assets/images/icon/s9.png";
import activity3 from "assets/images/superiority/activity-03.png";
import activity2 from "assets/images/superiority/activity-02.png";
import activity1 from "assets/images/superiority/activity-01.png";
import activity4 from "assets/images/superiority/activity-04.png";
import myPlain from "assets/images/superiority/my-plain.png";
import CustomActivityDialog from "./src/custom-activity-dialog.vue";
export default {
  components: {
    CustomActivityDialog
  },
  data() {
    return {
      clockInIcon,
      myPlain,
      active: "",
      activityList: [
        {
          imgSrc: activity2,
          id: 111,
          title: "活动名称民乐社团(样本范例)",
          tip: "选中打卡"
        },
        {
          imgSrc: activity1,
          id: 222,
          title: "英语社区民乐社团打卡任务",
          tip: "选中打卡"
        },
        {
          imgSrc: activity3,
          id: 333,
          title: "45天的持续打卡任务",
          tip: "选中打卡"
        },
        {
          imgSrc: activity4,
          id: 444,
          title: "英民国民乐社团小提琴打卡",
          tip: "选中打卡"
        },
        {
          imgSrc: activity2,
          id: 111,
          title: "活动名称民乐社团（样本范例）",
          tip: "选中打卡"
        },
        {
          imgSrc: activity1,
          id: 222,
          title: "英语社区民乐社团打卡任务",
          tip: "选中打卡"
        }
      ]
    };
  },
  methods: {
    handleClick(item, index) {
      this.active = index;
      this.$router.push({
        path: "/superiority-clockin/question",
        query: {
          id: item.id
        }
      });
    },
    customActivity() {
      this.$refs.cuttomActivityDialog.show();
    }
  }
};
</script>
<style lang="scss" scoped>
.g_main {
  width: 13.66rem;
  height: 100%;
  margin: 0 auto;
  overflow: hidden;
  padding: 0.2rem 0.1rem 0.29rem 0.2rem;
  box-sizing: border-box;
}
.superiority-clockin {
  width: 100%;
  height: 100%;
  display: flex;
}

.superiority-clockin__main {
  flex: 1;
  height: 100%;
  padding-top: 0.7rem;
  background-color: #fff;
  border: 1px solid rgba(228, 232, 237, 1);
  border-radius: 0.06rem;
  position: relative;
  .main-header {
    position: absolute;
    top: 0;
    left: 0;
    height: 0.7rem;
    line-height: 0.7rem;
    width: 100%;
    border-bottom: 1px solid rgba(228, 232, 237, 1);
    padding-left: 0.3rem;
    box-sizing: border-box;
    .header-title {
      font-size: 0;
      color: rgba(51, 51, 51, 1);
      img {
        height: 0.2rem;
        width: 0.2rem;
        vertical-align: middle;
      }
      span {
        font-size: 0.18rem;
        font-weight: bold;
        color: rgba(51, 51, 51, 1);
        height: 0.2rem;
        line-height: 0.2rem;
        display: inline-block;
        vertical-align: middle;
        margin-left: 0.12rem;
      }
    }
  }
  .main-content {
    height: 100%;
    width: 100%;
    position: relative;
  }
}

.superiority-clockin__asider {
  width: 2.33rem;
  height: 100%;
  margin-left: 0.12rem;
  background-color: #fff;
  border: 1px solid rgba(228, 232, 237, 1);
  display: flex;
  flex-direction: column;
  .asider-header {
    height: 0.71rem;
    line-height: 0.71rem;
    border-bottom: 1px solid rgba(228, 232, 237, 1);
    color: rgba(51, 51, 51, 1);
    font-size: 0.18rem;
    font-weight: bold;
    color: rgba(51, 51, 51, 1);
    text-align: center;
    .header-title {
      border-bottom: 1px solid rgba(228, 232, 237, 1);
    }
    .plain {
      width: 2.31rem;
      height: 0.7rem;
    }
  }
  .asider-main {
    height: 100%;
    display: flex;
    flex-direction: column;
    padding-top: 0.16rem;
    flex: 1;
    .activity-list {
      flex: 1;
      overflow: auto;
      &::-webkit-scrollbar-thumb {
        background-color: rgba(247, 151, 39, 0.2);
      }

      &::-webkit-scrollbar-thumb:window-inactive {
        background-color: rgba(247, 151, 39, 0.2);
      }

      .activity-list-item {
        display: flex;
        padding: 0.15rem 0.3rem 0.15rem 0.11rem;
        cursor: pointer;
        .left {
          width: 0.79rem;
          height: 0.58rem;
          display: inline-block;
        }
        .right {
          height: 0.58rem;
          flex: 1;
          margin-left: 0.11rem;
          .title {
            color: rgba(51, 51, 51, 1);
            line-height: 0.15rem;
            font-size: 0.13rem;
            word-break: break-all;
            text-align: left;
          }
          .tip {
            font-size: 0.12rem;
            color: rgba(153, 153, 153, 1);
            margin-top: 0.12rem;
          }
        }
      }
      .activity-list-item.is-active {
        background: rgba(247, 151, 39, 0.1);
      }
    }
    .asider-action {
      height: 1.3rem;
      padding-top: 0.11rem;
      button {
        display: block;
        height: 0.36rem;
        width: 1.41rem;
        border: 1px solid #f79727;
        background-color: #fff;
        cursor: pointer;
        border-radius: 0.18rem;
        font-size: 12px;
        outline: none;
        margin: 0 auto;
        color: #f79727;
        margin-top: 0.11rem;
        line-height: 0.34rem;
      }
      button:last-child {
        color: #999;
        border-color: #bbb;
      }
    }
  }
}
</style>



