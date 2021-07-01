<template>
  
  <Counter />
</template>

<script>
import Counter from './components/Counter.vue';

export default {
  components: {
    Counter
    }
  };

</script>

<style>

body {
  background: #333;
  font-family: 'Quicksand', sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  }
#app {
  width: 50%;
  height: 50vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  text-align: center;
  color: #f5f5f5;
  border-radius: 10px;
  background: rgba(65, 62, 62, 0.5);
  box-shadow: 0px 0px 79px 5px rgba(228,98,44,0.49);
  position: relative;

}
</style>
