<template>
  <form ref="studentForm">
    <label for="fname">Предмет:</label>
    <input type="text" v-model="urok" name="urok" placeholder="urok">

    <label for="lname">Кредиты:</label>
    <input type="text" v-model="kredity" name="kredity" placeholder="kredity">

    <label for="lname">Преподаватель:</label>
    <input type="text" v-model="prerodavatel" name="prerodavatel" placeholder="prerodavatel">


    <input type="submit" title="submit" @click="post">
  </form>
</template>

<script>
export default {
  data(){
    return{
      urok: '',
      kredity: 0,
      prerodavatel: '',
    }
  },
  methods: {
    post(){
      console.log({urok: this.urok ,kredity: this.kredity,vprorodavatel: this.prerodavatel})

      fetch("http://127.0.0.1:8000/urok",{
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({ urok: this.urok ,kredity: this.kredity,prerodavatel: this.prerodavatel})
      })
        .then((response) => response.json())
        .then((data) => {
          console.log('Success:', data);
        })
        .catch((error) => {
          console.error('Error:', error);
        });
    }
  }
}
</script>

<style scoped>
form{
  padding: 50px 0 0 0;
}
label{

}
input[type=text], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=submit] {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}

div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
</style>
