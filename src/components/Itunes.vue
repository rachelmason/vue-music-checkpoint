<template>
<div>
    <h2> 🎵 search</h2>
    <form  @submit.prevent="getMusic(artist)"class="col s12">
        <div class="input-field col s6">
        <input v-model="artist" type = "text" placeholder="artist">
        </div>
        <button class="waves-effect waves-light btn" type="submit">get music</button>
    </form>
        <Song v-for="song in songs" :song="song">
        </Song>

</div>

</template>

<script>  
import itunesService from '../services/itunes-service' 
import Song from './Song'
export default {
    name: 'itunes',
    components: {Song},
    data(){
        return{
            songs: []
        }
    },
    methods: {
        getMusic(artist){ 
            itunesService.getMusicByArtist(artist).then(res=>{
                
                console.log(res)
                res.json().then(res=>{
                 var songList = res.results.map(function (song) {

                  return {
                      title: song.trackName,
                      albumArt: song.artworkUrl60,
                      artist: song.artistName,
                      collection: song.collectionName,
                      price: song.collectionPrice,
                      preview: song.previewUrl,
                      id: song.trackId,
                      vote: 0
                    }
                       


                })

this.songs = songList
console.log(songList)

                })
                
            })
        }
    }
      
}

</script>

<style scoped> 
.btn{
   background-color: #ef9a9a
}
.btn:hover{
   background-color: #ef9a9a
}
.btn:focus{
   background-color: #ef9a9a
}

 /* label color */
   .input-field label {
     color: #ef9a9a;
   }
   /* label focus color */
   .input-field input[type=text]:focus + label {
     color: #ef9a9a;
   }
   /* label underline focus color */
   .input-field input[type=text]:focus {
     border-bottom: 1px solid #ef9a9a;
     box-shadow: 0 1px 0 0 #ef9a9a;
   }
   /* valid color */
   .input-field input[type=text].valid {
     border-bottom: 1px solid #ef9a9a;
     box-shadow: 0 1px 0 0 #ef9a9a;
   }
   /* invalid color */
   .input-field input[type=text].invalid {
     border-bottom: 1px solid #ef9a9a;
     box-shadow: 0 1px 0 0 #ef9a9a;
   }
   /* icon prefix focus color */
   .input-field .prefix.active {
     color: #ef9a9a;
   }


</style>