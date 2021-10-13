<template>
        <v-data-table
        :headers="headers"
        :items="data"
        :items-per-page="5"
        class="elevation-1 mt-15 pa-5"
        ></v-data-table>
</template>
<script>
export default {
    data(){
        return{
            data:[],
            headers:[
                {
                    text: 'File Name',
                    align: 'start',
                    sortable: false,
                    value: 'name',
                },
                {
                    text: 'Classification Name',
                    align: 'start',
                    sortable: false,
                    value: 'name',
                },
                {
                    text: 'Confidence level',
                    align: 'start',
                    sortable: false,
                    value: 'name',
                },
            ]
        }
    },
    async created(){
        try{
            const response = await this.$axios.get('infer')
            if(response.response)
                this.data = response.response.data
        }catch(e){
            console.log(e)
        }
    }
}
</script>