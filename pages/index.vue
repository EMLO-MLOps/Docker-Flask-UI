<template>
  <v-row class="mt-15" justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
       
      </v-card>
      <v-card >
        <v-card-title class="headline">
          Upload Documents
        </v-card-title>
        <v-card-text>
          <v-file-input
            multiple
            outlined
            v-model="file"
            dense
            label="Upload Files"
          ></v-file-input>
          <v-row align="center" justify="center">
            <v-col md="2">
              <v-btn @click="uploadFile()" color="primary">Upload</v-btn>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data(){
    return{
      file:null
    }
  },
  methods:{
    async uploadFile(){
      try{
        const formData = new FormData()
        for (let i in this.file) {
          formData.append("documents[" + i + "]file", this.file[i].file)
        }
        const response = await this.$axios.post('upload-api', formData)
      }catch(e){
        console.log(e)
      }
    }
  }
}
</script>
