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
              <tr>
                  <td v-if="items.length == 0">
                      <h3>No hobies found</h3>
                  </td>
              </tr>
      </tbody>
  
  </table>
</template>

<script>
export default {
     data(){
            return{
                items: [
                    {'id': 1, 'hobbyName': 'Music', 'hobbyDescription': 'My music hobby'}, 
                    {'id': 2, 'hobbyName': 'Reading', 'hobbyDescription': 'My reading hobby'}
                ],
                vegetables: ['aloo', 'pyaaz', 'gobi'],
                employee: {'firstName': 'Madhuri', 'lastName': 'Pandey'},
                listEmployees: [
                    {'firstName': 'Madhuri', 'lastName': 'Pandey', 'company': 'TCS'}, 
                    {'firstName': 'Pooja', 'lastName': 'Pandey', 'company': 'TCS'}, 
                    {'firstName': 'Rahul', 'lastName': 'Pandey', 'company': 'SCB'}
                ]
            }
        },
    name: 'Index',
    mounted(){
        
      // this.fetchHobby();
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

