<template>
 
  <div class="content-box">
    <div class="content">
      <PageHeader/>
      <PageContent/>
    </div>

  </div>
</template>

<script>
import { defineComponent } from 'vue';
import PageHeader from './components/PageHeader.vue'
import PageContent from './components/PageContent.vue'

export default defineComponent({
  name: 'App',
  components: {
    PageHeader,
    PageContent
  }
})
</script>
// why does body work? look it up online later
// the bottom half of body is what confuses me

// also why body and container separated
<style>
 
  .content-box{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    padding: 0;
  }
  
  .content{
    min-height: 600px;
    width: 500px;
    overflow: auto;
    border-radius: 5px;
    box-shadow: 1px 2px 3px 4px rgba(12,12,12,0.2);
  }
</style>
