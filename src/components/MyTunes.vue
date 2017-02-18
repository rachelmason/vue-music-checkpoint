<template>

    <div>
<h2> my 🎵</h2>
<div v-for="song in mySongs">
    <div class="row">
    <div class="col s12 m6">
      <div class="card">
        <div class="card-image">
          <img :src="song.albumArt">
          <span class="card-title">{{song.title}} </span>
          <button class="btn-floating halfway-fab waves-effect waves-light" @click="removeSong(song)"><i class="material-icons">remove</i></button>
        </div>
        <div class="card-content">
          <p>{{song.collection}}</p>
          <audio controls>
<source :src="song.preview" type="audio/mp4">
</audio>
<br>
<a @click="upSong(song)"><i class ="material-icons colPink">thumb_up</i></a>
{{song.upVote}}
<a @click="downSong(song)"><i class ="material-icons colPink">thumb_down</i></a>
{{song.downVote}}
        </div>
      </div>
    </div>
  </div>
</div>

    </div>
</template>
<script>
import myTunesService from '../services/mytunes-service' 
import Song from './Song'
export default {
    name: 'myTunes',
    components: {Song},
    data(){
        return{
            mySongs: myTunesService.getTracks()
        }
    },
    methods: {
       removeSong(song){
           myTunesService.removeTrack(song)

       },
       upSong(song){
            if(song){
                song.upVote ++
                console.log(song.upVote)
                
            }

       },
        downSong(song){
            if(song){
                song.downVote ++
              
            }
       }
    }
      
}


</script>

<style scoped>

    .btn-floating{
        background-color:  #ef9a9a
    }
     .colPink{
        color:  #ef9a9a
    }
  

.card .card-image .card-title {
    color: rgb(192, 193, 196);
    font-weight: bold
}
.row .col.m6{
    width: 50%
}
audio{
    width: 75%
}


</style>