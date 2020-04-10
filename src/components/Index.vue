<template>
  <table>
      <thead>
          <tr>
              <td>Id</td>
              <td>Hobby Name</td>
              <td>Hobby Description</td>
          </tr>
      </thead>
          <tbody>
              <tr v-for="item in items" :key="item.id">
                  <td>{{item.id}}</td>
                  <td>{{item.hobbyName}}</td>
                  <td>{{item.hobbyDescription}}</td>
              </tr>
      </tbody>
  
  </table>
</template>

<script>
export default {
     data(){
            return{
                items: []
            }
        },
    name: 'Index',
    mounted(){
        
       this.fetchHobby();
    },
 methods:{
     fetchHobby(){
       //  debugger;
         let uri = "http://localhost:8080/api/getHobby";
         this.axios.get(uri).then((response) => {
             this.items = response.data;
         })
     }
 }
}
</script>

