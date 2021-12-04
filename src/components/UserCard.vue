<template>
    <q-card class="my-card" flat bordered style="min-width:450px">
      <q-item>
        <q-item-section avatar>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/boy-avatar.png">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label>{{ user.name }}</q-item-label>
          <q-item-label caption>{{ user.email }}</q-item-label>
        </q-item-section>
      </q-item>

      <q-separator />

      <q-card-section horizontal>
        <q-card-section class="items-center col-6">
          <q-icon name="place" style="font-size: 20px;" />
          {{ user.address.city }}
        </q-card-section>

        <q-separator vertical />

        <q-card-section class="col-8">
          {{ user.phone }}
        </q-card-section>
      </q-card-section>
    </q-card>
</template>

<script>

export default({
  name: 'UserCard',
  props:['user'],
  data(){
    return{

    }
  },
  methods:{

  },
  computed:{
    
  },
})
</script>
