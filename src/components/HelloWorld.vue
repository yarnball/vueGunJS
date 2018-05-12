<template>
  <div>
    <h1>{{ JSON.stringify(results) }}</h1>
    <button @click="getTod"> test </button>
  </div>
</template>

<script>
import Gun from 'gun/gun'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Gun.js',
      results: []
    }
  },
  mounted () {
    var gun = Gun('http://localhost:8080' + '/gun');
    var think = gun.get('think/');
    var _this = this
    think.on(function(thought, id){
          _this.results = Object.values(thought)
          console.log('TH', Object.values(thought))
    })
    
  },
  methods: {
    getTod (){
        console.log('test')
    }
  },

}
</script>