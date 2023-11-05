<template>
  <div>
    <div class="container">
      <ul class="nav-box">
        <li
          ref="navItem"
          v-for="(item, index) in data"
          :key="index"
          class="nav-item"
          :class="item.active ? 'active' : ''"
          @click="handleClick(index)"
        >
          {{ item.name }}
        </li>
        <div class="slider" :style="sliderStyle"></div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Vue2cliDaohang",

  data() {
    return {
      data: [
        { name: "首页", active: true },
        { name: "前端开发", active: false },
        { name: "数据库", active: false },
        { name: "数据结构与算法", active: false },
      ],
      sliderStyle: {
        width: "10px",
        left: "10px",
      },
    };
  },
  mounted() {
    this.changeSider();
  },

  methods: {
    handleClick(index) {
      this.data.forEach((item) => {
        item.active = false;
      });
      this.$set(this.data, index, { ...this.data[index], active: true });
      this.changeSider();
    },
    changeSider() {
      let activeIndex = this.data.findIndex((item) => {
        return item.active;
      });
      let navItem = this.$refs.navItem?.[activeIndex];
      this.sliderStyle = {
        width: navItem.offsetWidth - 36 + "px",
        left: navItem.offsetLeft + 18 + "px",
      };
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

.container {
  min-width: 600px;
  padding: 30px;
  box-shadow: 0 2px 16px #fff;
  border-radius: 20px;
  overflow-x: auto;
}
.nav-box {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  /* border-bottom: 2px solid rgba(229, 229, 229); */
  font-size: 18px;
  font-weight: 600;
  position: relative;
}
.nav-box .nav-item {
  font-size: 18px;
  font-weight: 600;
  list-style: none;
  padding: 18px;
  cursor: pointer;
}
.nav-box .nav-item.active,
.nav-item:hover {
  color: #64ccc5;
}
ist-view .content h2 {
  margin-bottom: 10px;
}
.slider {
  position: absolute;
  top: 59px;
  height: 5px;
  background-color: #64ccc5;
  border-radius: 10px;
  transition: all 0.3s ease-in-out;
  box-shadow: 0px -5px 8px 0px red;
}
</style>
