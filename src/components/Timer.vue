<template>

<div>
  <div class="btn-group"  style="padding:15px">
    <v-card-title 
    class="secondary green--text font-weight-light display-2 text-uppercase justify-center" >
    TRABELSI Oussama
    </v-card-title>

   <!--        
    <button
      @click="$emit('stop')"
      :disabled="state == 'stopped'"
    >Reset</button>
-->
	<div class="wrapper">

    <div class="box ">
        <h1>Today,{{currentDate()}}</h1>
    </div>

    <div class="box">

    <button
     @click="$emit('pause')"
     :disabled="state == 'stopped' || state == 'paused'"
     style="background-color:red"
    >Stop</button>

    <button
    @click="$emit('addTime') "
    :disabled="state == 'stopped'"
    >Start new</button>

    <button  
    @click="$emit('start')"
    :disabled="state == 'running'"
    >Start</button>
    </div>

    <div class="box">
      <h2 style="color:green">{{ timer }}</h2>
    </div>
  </div>
</div>

<table style="margin-right:50px" >
  <tr>
    <th>Periode</th>
    <th>Time</th>
  </tr>

  <tr >
    <td>current Periode</td> 
    <td style="color:green">{{ timer }}</td>  
  </tr>

  <tr v-for="lap in times" :key="lap.id" >
    <td>{{lap.title}} </td>
    <td>{{ lap.time }}</td>  
  </tr>

</table>

	<div class="total">
    <div class="box">    
    </div>
    <div class="totalNumber">
       <h2> total {{ totaltimer }} </h2>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Timer',
  props: ['timer', 'state','times','totaltimer'],
 
  methods:{
 // get date of today
 currentDate() {
      const current = new Date();
      const date = `${current.getDate()}/${current.getMonth()+1}/${current.getFullYear()}`;
      return date;
    }
  }
}
</script>

<style>
.btn-group button {
  background-color: #04AA6D; 
  border: 1px solid green; 
  color: white; 
  padding: 10px 24px; 
  cursor: pointer; 
  float: right; 
/*margin-bottom:10px;
  margin-top:10px;*/
}

table {
  border-collapse: collapse;
  border-spacing: 0;
  width: 100%;
  border: 1px solid #ddd;
}

th, td {
  text-align: left;
  padding: 16px;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

.wrapper {
  display: grid;
  grid-template-columns: 50% 30% 20%;	
}

.total {
  display: grid;
  grid-template-columns: 60% 40%;	
}
.box {
		padding: 1em;
}

.totalNumber {
		padding: 1em;
    color:green;
}

</style>
