<template>
  <div class="user-recording-zone-component-section">
    <button v-on:click="recording()" >Enregistrer</button>
    <button v-on:click="stop_recording()">Arreter</button>
    <button>Annuler</button>
    <button>Envoyer</button>
  </div>
</template>

<script>
export default {
name: "UserRecordingZoneContainerComponent",
  data(){
  return{
    bigcontainerforallaudio:null,
     recordingobject:null,
    Bloc:[],
    blocintoblob:null,
    makeurl:null,
    audio_to_read:null,
    audio_list:[
      {
        Num:0,
        audio_content:null,
      }
    ]
  }
  },
      methods:{
     recording(){
      navigator.mediaDevices.getUserMedia({audio:true})
          .then(stream=>{
            this.recordingobject = new MediaRecorder(stream);
            this.recordingobject.start()
            //Second step: Save recording piece in à table
            this.Bloc.length=0;
            this.recordingobject.addEventListener("dataavailable",event=>{
              this.Bloc.push(event.data);
            })
            //third step : Transform bloc variable into
            this.recordingobject.addEventListener("stop",()=>{
              this.blocintoblob = new Blob(this.Bloc);
              //five step: Create and url for new blob object
              this.makeurl = URL.createObjectURL(this.blocintoblob);
              this.audio_list.push({Num:this.Num++, audio_content:this.makeurl})
              this.audio_to_read= new Audio(this.makeurl);
              //TODO:Post audio information in audio_list list
              this.audio_to_read.play();
            })

     })


    },
        //TODO Post audio dato from audio_list to backend
       /* post_audio_list_to_back(){

        }*/
    stop_recording(){
       this.recordingobject.stop();
    },

}
}
</script>

<style scoped>


</style>