<script setup>
	import { ref } from 'vue'
	const response = ref({})

  // adding delay
  await new Promise(resolve => {
    setTimeout(() => { 
      resolve()
    }, 1000)
  })
    
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts/' +  Math.floor(Math.random() * 9)+1)
    console.log(res)
    response.value = (await res.json())
  } catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
  }

</script>

<template >
  <div class="card"> 
    <b>{{ response.title }} </b><hr/> 
    {{response.body}}
  </div>

</template>

<style>

.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  width: 20rem;
  padding:10px;
  margin:10px;
  background-color:pink;
}
</style>