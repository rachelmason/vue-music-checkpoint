<template>


<div class="row">
    <div class="col s12 m6">
      <div class="card">
        <div class="card-image">
          <img :src="song.albumArt">
          <span class="card-title">{{song.title}} </span>
          <button class="btn-floating halfway-fab waves-effect waves-light" @click="saveSong(song)"><i class="material-icons">add</i></button>
          
        </div>
        <div class="card-content">
          <p>{{song.collection}}</p>
          <audio controls>
<source :src="song.preview" type="audio/mp4">
</audio>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import myTunesService from '../services/mytunes-service'
import MyTunes from './MyTunes'
export default {
    name:'song',
    components: {MyTunes},
    props: ['song', 'mySongs'],
    methods: {
        saveSong(id){
            myTunesService.addTrack(id)
         
            
        }
    }
}

</script>
<style scoped>

 .btn-floating{
        background-color:  #ef9a9a
    }
.card .card-image .card-title {
    color: rgb(192, 193, 196);
    font-weight: bold
}
.row .col.m6{
    width: 50%
}
audio{
    width: 70%
}
</style>