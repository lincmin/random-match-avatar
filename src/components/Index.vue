<template>
  <div class="container">
    <div class="center">
      <toggle-button :value="false"
                     :color="color"
                     :labels="{checked: '开始', unchecked: '暂停'}"
                     :width="70"
                     :height="30"
                     @change="toggle" />
    </div>
    <div class="box">
      <div class="person"
           v-for="member in members"
           :key="member.name">
        <div class="line">
          <img :src="member.img"
               alt="">
          <span class="name">{{member.name}}</span>
        </div>
      </div>
    </div>
    <span class="loadWrap">
      <ring-loader :loading="loading"
                   :color="color"
                   :size="size"></ring-loader>
    </span>
  </div>
</template>

<script>
import RingLoader from 'vue-spinner/src/RingLoader.vue'
var running
export default {
  name: 'Index',
  components: {
    RingLoader
  },
  data () {
    return {
      loading: false,
      color: '#5dc596',
      size: '60px',
      members: [
        {
          name: '0',
          img: require('../assets/avatars/0.jpg')
        },
        {
          name: '1',
          img: require('../assets/avatars/1.jpg')
        },
        {
          name: '2',
          img: require('../assets/avatars/2.jpg')
        },
        {
          name: '3',
          img: require('../assets/avatars/3.jpg')
        },
        {
          name: '4',
          img: require('../assets/avatars/4.jpg')
        },
        {
          name: '5',
          img: require('../assets/avatars/5.jpg')
        },
        {
          name: '6',
          img: require('../assets/avatars/6.jpg')
        },
        {
          name: '7',
          img: require('../assets/avatars/7.jpg')
        },
        {
          name: '8',
          img: require('../assets/avatars/8.jpg')
        },
        {
          name: '9',
          img: require('../assets/avatars/9.jpg')
        },
        {
          name: '10',
          img: require('../assets/avatars/10.jpg')
        },
        {
          name: '11',
          img: require('../assets/avatars/11.jpg')
        },
        {
          name: '12',
          img: require('../assets/avatars/12.jpg')
        },
        {
          name: '13',
          img: require('../assets/avatars/13.jpg')
        },
        {
          name: '14',
          img: require('../assets/avatars/14.jpg')
        },
        {
          name: '15',
          img: require('../assets/avatars/15.jpg')
        },
        {
          name: '16',
          img: require('../assets/avatars/16.jpg')
        },
        {
          name: '17',
          img: require('../assets/avatars/17.jpg')
        },
        {
          name: '18',
          img: require('../assets/avatars/18.jpg')
        },
        {
          name: '19',
          img: require('../assets/avatars/19.jpg')
        }
      ]
    }
  },
  methods: {
    run () {
      var arr = this.members
      arr.sort(function () {
        return 0.5 - Math.random()
      })
      this.members = arr
    },
    start () {
      this.loading = true
      running = setInterval(() => {
        this.run()
      }, 200)
    },
    stop () {
      clearInterval(running)
      this.loading = false
    },
    toggle () {
      var load = this.loading
      if (!load) {
        this.start()
      } else {
        this.stop()
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  width: 100%;
  height: 100%;
}
.box {
  margin: 0 30px;
  display: flex;
  flex-wrap: wrap;
}
.person {
  position: relative;
}
.person .line {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}
.person:nth-child(odd) {
  float: left;
}
.person:nth-child(odd) .line:after {
  content: '';
  position: absolute;
  top: 50%;
  right: 0;
  background: #5dc596;
  width: 20%;
  height: 2px;
}
.person:nth-child(even) {
  float: right;
}
.person:nth-child(even) .line:after {
  content: '';
  position: absolute;
  top: 50%;
  left: 0;
  background: #5dc596;
  width: 20%;
  height: 2px;
}
.person .line > img {
  width: 150px;
  height: 150px;
}
.name {
  color: #5dc596;
}
.loadWrap {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
