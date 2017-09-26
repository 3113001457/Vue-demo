<template>
  <div id="secondcomponent">
    <h1>I am another page</h1>
    <a> written by {{ author }} </a>
    <div>饿热热热热热热热</div>
    <p v-for="item in arr">{{item}}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      author: "微信公众号 jinkey-love",
      arr: []
    }
  },
  mounted: function() {
    this.$http.jsonp('https://api.douban.com/v2/movie/top250?count=10', {}, {
        headers: {

        },
        emulateJSON: true
    }).then(function(response) {
      // 这里是处理正确的回调
      console.log(response.data.subjects[0].rating)
        this.arr = response.data.subjects[0].rating
        // this.arr = response.data.subjects"] 也可以

    }, function(response) {
        // 这里是处理错误的回调
        console.log(response)
    });
  }
}
</script>