<template>
  <div id="app">  
     
     <Picture />
     <!-- <event-card/> -->
  </div>
</template>

<script>
import Picture from './components/Picture'
// import EventCard from './components/EventCard.vue'


export default {
  name: 'App',
  components: {
    Picture
    // EventCard //its just test (uncomment them)
       
 
  
    
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  margin-top: 60px;

}
.btn{

 color: black;
	padding: 40px 80px;
	font-family: sans-serif;
	Text-decoration: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 15px;
  font-family: inherit;
}
</style>
