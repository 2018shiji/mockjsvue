<template>
    <ul>
        <li v-for="item in data" v-bind:key="item">{{item}}</li>
        <li>Response: {{result}}</li>
    </ul>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
        data: [],
        result: '',
        param: {username: 'username', password: 'password'}
    }
  },
  mounted() {
    axios.get('/api/data').then(res => {
        this.data = res.data;
        console.log(res.data);
        console.log(this.data)
    });
    axios.post('/api/postData', this.param).then(resp => {
        this.result = resp.data;
        console.log(resp);
        console.log(resp.data);
    })
  },
  method() {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
