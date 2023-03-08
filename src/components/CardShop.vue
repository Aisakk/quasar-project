<template>
    <q-card class="my-card">
        <q-card-section class="flex justify-between items-end">
          <img :src="img" :alt="description"/>
            <p>{{ description  }}</p> 
           <p>${{ value }}</p>
        </q-card-section>
        <q-separator dark inset />
      </q-card>
</template>
<script>
export default {
  props:['img', 'description', 'value', 'total'],
  setup (props) {
    console.log(props.img, props.description, props.value)
   }
    
}
</script>
