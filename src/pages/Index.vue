<template>
  <div class="q-ma-md">
    <q-input outlined v-model="search" placeholder="Please enter your request">
      <template v-slot:prepend>
       <q-icon v-if="search === ''" name="search" />
       <q-icon v-else name="clear" class="cursor-pointer" @click="search = ''" />
      </template>
    </q-input>
    <div class="flex q-mt-xl q-gutter-xl justify-center">
      <UserCard
        v-for="(user,idx) in compData" 
        :key="idx"
        :user="user"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import UserCard from '../components/UserCard.vue'
export default ({
  components:{ UserCard },
  name: 'PageIndex',
  data(){
    return{
      search: '',
      dataset: false,
    }
  },
  methods:{
  },
  computed:{
    compData(){
      if (this.search === '') return this.dataset
      else{
        let searchedArr = []
        Object.values(this.dataset).forEach(el=>{
          if(JSON.stringify(el).includes(this.search)) return searchedArr.push(el)
        })
        return searchedArr
      }
    }
  },
  async mounted(){
    this.dataset = await axios.get('https://jsonplaceholder.typicode.com/users').then(function(res){
      return res.data
    })
  }
})
</script>
