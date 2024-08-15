<template>

  <div class="layout">

    <h1>Inserte los topics</h1>

    <InputTag @onTagsChange="handleOnTagsChange"></InputTag>

  </div>
  
</template>

<script>

import InputTag from './components/InputTag.vue';

export default{

  components:{
    InputTag
  },

  methods:{

    handleOnTagsChange(tags){
      console.log(tags)
    },

  }

}

</script>

<style scoped>

.layout{
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: #333;

  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

h1{
  font-size: 2.6rem;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  font-weight: 600;
  letter-spacing: 1px;
  color: white;
  text-decoration: underline;
  text-decoration-color: yellow;
}

</style>
