<template>
  <div class="home">
    <div ref="banner" class="banner content-item-block">
      <div class="video-wrapper">
        <video
          ref="video"
          class="video"
          preload="auto"
          muted
          loop
          playsinline
          autoplay
          poster="http://www.yanmaixianwei.com/images/green_oat_field.jpg"
          src="http://www.yanmaixianwei.com/video/cloudskyhill.mp4"
          tabindex="-1"
        ></video>
      </div>
      <h1 class="banner-title">
        在北美生长着古老的作物燕麦
        <div class="subTitle">CLOUD SKYHILL 云天山</div>
      </h1>
      <div class="search">
        <input-search @search="searchJobs" placeholder="输入燕麦搜索"></input-search>
      </div>
      <div class="bottom-tips">
        <span class="arrow-down" @click="scrollDown">
          <i>⤓</i>
        </span>
        <span class="vertical-dashed"></span>
      </div>
    </div>

    <!-- 产品 -->
    <div class="main">
      <div ref="product" class="product content-item-block">
        <h1 class="title">北美天然燕麦纤维</h1>
        <div class="desc">云天山美国燕麦纤维粉，利用美国世界顶级的先进工艺技术生产，加工过程中不涉及任何化学、化工原料、不添加任何防腐剂、色素、调味剂</div>
        <ul class="product-list">
          <li
            class="product-item"
            v-for="(item, key) in products"
            :key="key"
            @click="jumpToDetail(item)"
          >
            <img :src="item.logo" alt />
            <div>{{ item.title }}</div>
          </li>
        </ul>
        <router-link to="/products">
          <div class="more">
            <!-- <span class="more-button">云天山燕麦纤维</span> -->
            <bytedance-button size="large">云天山燕麦纤维</bytedance-button>
          </div>
        </router-link>
      </div>

      <!-- 云天山燕麦纤维 -->
      <div class="job-category content-item-block">
        <h2 class="job-category-title title">云天山燕麦纤维222</h2>
        <ul class="job-category-list clearfix">
          <li v-for="item in jobCategories" :key="item.id" class="job-category-item">
            <router-link :to="{ name: 'jobs', params: { job_category_id: item.id } }">
              <div class="image" :style="`backgroundImage:url(${item.image})`">
                <span class="overlay" v-if="!item.id">{{ item.zh_name }}</span>
              </div>
              <div v-if="item.id" class="name">{{ item.zh_name }}</div>
            </router-link>
          </li>
        </ul>
      </div>

      <!-- 云天山燕麦纤维 -->
      <div class="byteStandard content-item-block">
        <h1 class="title">云天山燕麦纤维</h1>
        <div class="desc">燕麦纤维是一种优质的膳食纤维，低甜味、低热量、无异味，能有效限制消化道内脂肪的吸收，促进类脂化合物的排泄，增加饱腹感</div>
        <div class="content">
          <div class="image">
            <span
              v-show="productLayerVisible"
              class="layer"
              @animationend="onScrollRightAnimationEnd"
            ></span>
            <img
              v-if="byteStandards[byteStandardActiveIndex]"
              width="100%"
              height="100%"
              :src="byteStandards[byteStandardActiveIndex].image"
              alt
            />
          </div>
          <div class="indicator">
            <ul>
              <li class="indicator-item" v-for="(item, index) in byteStandards" :key="index">
                <h3
                  :class="{ active: byteStandardActiveIndex === index }"
                  @click="
                  () => {
                    byteStandardActiveIndex = index;
                    productLayerVisible = true;
                  }
                "
                >{{ item.title }}</h3>
                <p v-html="item.content" v-show="byteStandardActiveIndex === index"></p>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- 云天山燕麦纤维 -->
      <div class="byteLife content-item-block">
        <h1 class="byteLife-title">云天山燕麦纤维</h1>
        <div class="block-item block-item-one">
          <div class="block-item-column block-item-column-text">
            <h2 class="block-item-column-title">云天山燕麦纤维</h2>
            <div class="content">
              <div class="content-item">
                <h2 class="content-item-title">云天山燕麦纤维</h2>
                <p class="content-item-desc">云天山燕麦纤维</p>
              </div>
              <div class="content-item">
                <h2 class="content-item-title">云天山燕麦纤维</h2>
                <p class="content-item-desc">云天山燕麦纤维</p>
              </div>
              <div class="content-item">
                <h2 class="content-item-title">云天山燕麦纤维</h2>
                <p class="content-item-desc">云天山燕麦纤维</p>
              </div>
            </div>
          </div>
          <div class="block-item-column block-item-column-image">
            <img src="http://www.yanmaixianwei.com/images/green_oat_field.jpg" alt />
          </div>
        </div>

        <div class="block-item block-item-one">
          <div class="block-item-column block-item-column-text">
            <h2 class="block-item-column-title">云天山燕麦纤维</h2>
            <div class="content">
              <div class="content-item">
                <h2 class="content-item-title">云天山燕麦纤维</h2>
                <p class="content-item-desc">云天山燕麦纤维</p>
              </div>
              <div class="content-item">
                <h2 class="content-item-title">云天山燕麦纤维</h2>
                <p class="content-item-desc">云天山燕麦纤维</p>
              </div>
              <div class="content-item">
                <h2 class="content-item-title">云天山燕麦纤维</h2>
                <p class="content-item-desc">云天山燕麦纤维</p>
              </div>
            </div>
          </div>
          <div class="block-item-column block-item-column-image">
            <img src="http://www.yanmaixianwei.com/images/green_oat_field.jpg" alt />
          </div>
        </div>
      </div>

      <!-- 云天山燕麦纤维 -->
      <div class="staffStory content-item-block">
        <h2 class="title">云天山燕麦纤维</h2>
        <ul class="staffStory-list clearfix">
          <router-link
            tag="li"
            :to="`/staff-stories/${item.id}`"
            v-for="item in staffStories"
            :key="item.id"
            class="staffStory-item"
          >
            <div class="avatar">
              <img width="100%" :src="item.avatar" alt srcset />
            </div>
            <div class="text">
              <h2 class="title">{{ item.title }}</h2>
              <div class="desc">{{ item.name }}&nbsp;|&nbsp;{{ item.department }}</div>
              <p class="remark">{{ item.remark }}</p>
            </div>
            <div class="circular-button">→</div>
          </router-link>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { watchScrollDirection } from "@/helper/utilities.js";

export default {
  name: "home",
  data() {
    return {
      productLayerVisible: true,
      search: "",
      products: [],
      jobCategories: [],
      byteStandards: [],
      byteStandardActiveIndex: 0,
      staffStories: []
    };
  },
  created() {
    const fetchProducts = this.request
      .get("/products")
      .then(response => {
        this.products = response;
      })
      .catch();
    const fetchJobCategories = this.request
      .get("/job-categories")
      .then(response => {
        this.jobCategories = response;
      });
    this.request.get("/byte-standards").then(response => {
      this.byteStandards = response;
    });
    this.request.get("/staff-stories").then(response => {
      this.staffStories = response;
    });
  },
  methods: {
    onScrollRightAnimationEnd() {
      this.productLayerVisible = false;
    },
    scrollDown() {
      this.$refs.product.scrollIntoView({
        behavior: "smooth",
        block: "start"
      });
    },
    searchJobs(keyword) {
      this.$router.push({ name: "jobs", params: { keyword } });
    },
    jumpToDetail(item) {
      this.$router.push({ name: "products", params: item });
    }
  },
  mounted() {
    const rootVm = this.$root;
    rootVm.$emit(
      "home-scrolling",
      { directionX: 1, directionY: -1 },
      { x: document.body.scrollLeft, y: document.body.scrollTop }
    );
    this.unwatch = watchScrollDirection(window, function(...args) {
      rootVm.$emit("home-scrolling", ...args);
    });
  },
  destroyed() {
    this.unwatch();
  }
};
</script>

<style lang="less" scoped>
@keyframes verticalMotion {
  0% {
    transform: translateY(6px);
  }
  50% {
    transform: translateY(-6px);
  }
  100% {
    transform: translateY(6px);
  }
}
@keyframes scrollToRight {
  0% {
    left: -100%;
  }

  100% {
    left: 100%;
  }
}

.home {
  .main {
    width: @main-width;
    margin: auto;
  }
  .content-item-block {
    .title {
      font-size: @font-size-larger;
    }
  }
}

.banner {
  height: 100vh;
  min-height: 400px;
  min-width: @main-width;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: rgba(51, 112, 255, 0.2);
  position: relative;
  .video-wrapper {
    font-size: 0;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: -1;
    overflow: hidden;
    .video {
      object-fit: cover;
      width: 100%;
      height: 100%;
    }
  }
  &-title {
    color: #fff;
    font-size: 60px;
    text-align: center;
    .subTitle {
      &::after,
      &::before {
        content: "";
        position: absolute;
        background-image: linear-gradient(
          270deg,
          hsla(0, 0%, 100%, 0),
          #fff 47%,
          hsla(0, 0%, 100%, 0)
        );
        height: 2px;
        width: 89px;
        top: 50%;
        transform: translateY(-50%);
      }
      &:before {
        right: 10px;
      }
      &:after {
        left: 10px;
      }
      position: relative;
      margin-top: 10px;
      font-size: @font-size-base;
      letter-spacing: 20px;
    }
  }
  .search {
    width: 500px;
    margin-top: 100px;
    margin-bottom: 40px;
  }
  .bottom-tips {
    position: absolute;
    bottom: 30px;
    width: 50px;
    height: 50px;
    flex-shrink: 0;

    text-align: center;
    .arrow-down {
      display: block;
      margin-bottom: 4px;
      width: 100%;
      height: 100%;
      border-radius: 50%;
      border: 1px solid #fff;
      text-align: center;
      line-height: 40px;
      color: #fff;
      cursor: pointer;
      font-size: 21px;
      i {
        animation: verticalMotion 1.3s infinite linear;
        display: inline-block;
        font-style: normal;
      }
    }
    // 分割竖线
    .vertical-dashed {
      border-left: 1px dashed #fff;
      height: 30px;

      display: inline-block;
    }
  }
}

// 云天山燕麦纤维
.product {
  margin-top: 40px;
  text-align: center;
  padding: 40px 40px;
  background: url(//);
  background-size: 100%;
  background-repeat: no-repeat;
  background-position: 0 370px;
  .desc {
    margin: 40px 0;
  }
  &-list {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }
  &-item {
    width: 90px;
    // height: 90px;
    cursor: pointer;
    &:nth-child(1),
    &:nth-child(9) {
      margin-top: 116px;
    }
    &:nth-child(2),
    &:nth-child(8) {
      margin-top: 80px;
    }
    &:nth-child(3),
    &:nth-child(7) {
      margin-top: 55px;
    }
    &:nth-child(4),
    &:nth-child(6) {
      margin-top: 30px;
    }
    &:hover {
      color: @main-color;
      img {
        border-radius: 19px;

        transform: scale(1.2);
        transform-origin: bottom;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
      }
    }
    img {
      width: 90px;
      height: 90px;
      border-radius: 19px;

      margin-bottom: 10px;
      transition: transform 0.3s;
    }
  }
  .more {
    margin: auto;
    margin-top: 170px;

    width: 149px;
  }
}

// 云天山燕麦纤维

.job-category {
  text-align: center;
  margin-top: 90px;

  &-list {
    margin-top: 70px;
  }
  &-item {
    float: left;
    margin-bottom: 16px;
    .image {
      width: 250px;
      height: 250px;
      line-height: 250px;
      background-repeat: no-repeat;
      background-size: 100%;
      border-radius: 50%;
      margin: 0 auto;

      transition: all 0.3s;
      background-position: center;
      overflow: hidden;
      &:hover {
        box-shadow: 0 0 8px 1px #ccc;
        background-size: 110%;
        & + .name {
          color: @main-color;
        }
      }
      .overlay {
        display: inline-block;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        color: #fff;

        font-size: 40px;
      }
    }
    .name {
      margin-top: 23px;
      font-size: @font-size-large;
    }
    margin: 0 2.5%;
    margin-bottom: 30px;
    width: 20%;
  }
}

// 云天山燕麦纤维

.byteStandard {
  padding: 40px 40px;
  overflow: hidden;
  .title {
    margin-bottom: 30px;
  }
  .desc {
    margin-bottom: 40px;
  }
  .content {
    .image {
      .layer {
        // left: -100%;
        width: 100%;
        top: 0;
        bottom: 0;
        background: rgba(255, 255, 255, 0.8);
        position: absolute;
        animation: scrollToRight 0.8s ease-in-out;
      }

      position: relative;

      float: left;
      width: 700px;
      height: 450px;
      margin-right: 100px;
      overflow: hidden;
      img {
        border-radius: 6px;
        object-fit: cover;
      }
    }
  }
  .indicator {
    color: #aaa;

    &-item {
      margin: 32px 0;
      h3 {
        &.active {
          color: black;
          font-size: 32px;
          font-weight: 400;
        }
        cursor: pointer;
      }
    }
  }
}
// 云天山燕麦纤维
.byteLife {
  // width:1200px;
  // overflow: hidden;
  &-title {
    margin-bottom: 70px;
  }
  padding-left: 10%;
  .block-item {
    overflow: hidden;
    margin-bottom: 100px;
    &:nth-child(odd) {
      .block-item-column {
        &-text {
          margin-right: 9%;
        }
        float: left;
      }
    }
    &:nth-child(even) {
      .block-item-column {
        &-image {
          margin-right: 9%;
        }
        float: right;
      }
    }

    &-column {
      &-title {
        margin-bottom: 40px;
        padding-bottom: 40px;
        border-bottom: 1px solid #ccc;
      }
      &-text {
        width: 30%;
      }
      &-image {
        height: 400px;
        width: 59%;
        border-radius: 8px;
        overflow: hidden;
        img {
          height: 100%;
          object-fit: cover;
        }
      }
    }
  }
}
// 云天山燕麦纤维
.staffStory {
  padding: 0 140px;
  .title {
    text-align: center;
    margin-bottom: 10px;
  }

  &-list {
    text-align: center;
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
  }
  &-item {
    // height: 450px;
    overflow: hidden;
    padding: 30px;
    width: 30%;
    cursor: pointer;

    &:hover {
      box-shadow: 0 10px 30px 0 @box-shadow-hover-color;
      .circular-button {
        color: @main-color;
      }
    }
    .avatar {
      width: 70%;
      margin: auto;
    }
    .text {
      .title {
        color: @primary-text-color;
        font-weight: @font-weight-regular;
        font-size: @font-size-large;
        margin: 10px 0;
        white-space: nowrap;
      }
      .desc {
        color: @primary-text-color;
        margin: 12px 0;
        font-size: @font-size-base;
      }
      .remark {
        font-size: @font-size-base;

        color: @regular-text-color;
        -webkit-box-orient: vertical;
        display: -webkit-box;
        -webkit-line-clamp: 3;
        overflow: hidden;
        text-overflow: ellipsis;
      }
    }
    .circular-button {
      border-radius: 50%;
      width: 30px;
      height: 30px;
      border: 1px solid;
      line-height: 30px;

      margin: auto;
      margin-top: 20px;
      color: #ccc;
    }
  }
}
</style>
