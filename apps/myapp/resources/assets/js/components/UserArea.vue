<template>
  <div id="userArea">
    <HeaderBar />
    <el-container>
      <transition
        mode="out-in"
        enter-active-class="fadeIn"
        leave-active-class="fadeOut"
        appear>
        <router-view class="animated"/>
      </transition>
    </el-container>
  </div>
</template>

<script>

import HeaderBar from './UserArea/HeaderBar.vue'
import { mapState } from 'vuex'

export default {
  name: 'UserArea',
  components: {
    HeaderBar
  },
  computed: {
    ...mapState(['loggedIn'])
  },
  mounted () {
    console.log('UserArea', this.loggedIn)
    if (!this.loggedIn) {
      this.$router.push('/admin/')
      return
    }
  }
}
</script>

<style >

  .el-header > h1{
    margin-bottom: 20px;
    margin-left: 5px;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

    h2 {
        font-size:26px;
    }

    h2 > small {
        font-size:14px;
        font-weight:normal;
        padding-left:10px;
        padding-top:10px;
    }
</style>
