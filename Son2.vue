<template>
    <div class="box">
        <h2>Son2 子组件</h2>
        从vuex中获取的值:<label>{{ count }}</label>
        <br />
        <button @click="addCount(-1)">值 - 1</button>
        <button @click="addCount(-5)">值 - 5</button>
        <button @click="addCount(-10  )">值 - 10</button>
        <button @click="changeCountAction(666)">一秒后修改成666</button>
        <button @click="changeCountAction(10000)">一秒后修改成10000</button>

        <button @click="newTitle(title)">改标题</button>
        <hr>
        <div>{{ userInfo.name }}</div>
<hr>
<div>{{ UpperCaseName }}</div>
<hr>
<div>{{ theme }}</div>
<button @click="setTheme">更新主题色</button>
    </div>
</template>

<script>
import { mapState, mapMutations, mapActions, mapGetters } from 'vuex'
export default {
  name: 'Son2Com',
  computed: {
    ...mapState(['count', 'user', 'setting']),
    ...mapState('user', ['userInfo']),
    ...mapGetters('user', ['UpperCaseName']),
    ...mapState('setting', ['theme'])
  },
  methods: {
    ...mapMutations(['addCount', 'newTitle']),
    ...mapMutations('setting', ['setTheme']),
    ...mapActions(['changeCountAction'])
    // changeTheme () {
    //   this.$store.commit('setting/setTheme')
    // }
    // handDel (n) {
    //   this.addCount(n)
    // },
    // change (title) {
    //   title = prompt('请输入你想改的标题')
    //   this.newTitle(title)
    // }
    // handleChange (num) { +
    //   this.$store.dispatch('changeCountAction', num)
    // }
  }
}
</script>

<style lang="css" scoped>
.box {
    border: 3px solid #ccc;
    width: 400px;
    padding: 10px;
    margin: 20px;
}

h2 {
    margin-top: 10px;
}
</style>
