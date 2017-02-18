<template>
 <div class="container">

  <div class="home">
    <!-- YOU WILL PROBABLY END UP WITH SOMETHING LIKE THIS -->
    <itunes class="itunes"></itunes>
    <my-tunes class="my-tunes"></my-tunes>
 

 </div>

 </div>
</template>

<script>
import Itunes from './Itunes'
import MyTunes from './MyTunes'
import itunesService from '../services/itunes-service'
export default {
  name: 'home',
  components:{Itunes, MyTunes},
  data () {
    return {
      
    }
  }
}
</script>



<style>

.home{
  display: flex;
  justify-content: space-between
  
  


}

.my-tunes{
  
  min-height: 500px;
  min-width: 50%;
  
}

.itunes{
  min-height: 500px;
  min-width: 45%;
  
}

</style>
