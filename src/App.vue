<template>
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplahsScreen/>
    </template>
  </Suspense>  
</template>

<script>
import SplahsScreen from '@/components/SplashScreen';
import { defineAsyncComponent } from 'vue';

export default{
  components: { 
    SplahsScreen ,
    Home: defineAsyncComponent(() => 
      new Promise((resolve) =>{
        setTimeout(() =>{
          resolve(import('./components/Home.vue'))
        },1000)
      } )
    )
  },

}


</script>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
