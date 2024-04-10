<template>
  <form @submit.prevent="handleSubmit">

    <label>Email:</label>
    <input type="email" required v-model="email">

    <label>password:</label>
    <input type="password" required v-model="password">
    <p class="error" v-if="passwordError">{{ passwordError }}</p>

    <label >Role:</label>
    <select required v-model="role">
        <option value="developer">web developer</option>
        <option value="designer">UI/UX designer</option>
        <option value="project Manager">Project Manager</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keypress="addskill">

    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
        <input type="checkbox" required v-model="terms">
        <label>Accept terms and conditions</label>
    </div>
   
    <div class="submit">
        <button>Create an Account</button>
    </div>
    
  </form>

  <p>email: {{ email }}</p>
  <p>password: {{ password}}</p>
  <p>role:{{ role }}</p>
  <p>Terms:{{ terms }}</p>
  

</template>

<script>
export default {
 data () {
    return {
     email:'',
     password:'',
     role: '',
     terms: false,
     tempSkill: '',
     skills:[],
     passwordError:''
    }
 },
 methods:{
    addskill (e){
    
        if(e.key === 'Enter' && this.tempSkill){
            if(!this.skills.includes(this.tempSkill)){
             this.skills.push(this.tempSkill)
        }
        this.tempSkill = ''
    }
 },
   deleteSkill (skill){
   this.skills.splice(this.skills.indexOf(skill), 1)
   },

   handleSubmit (){
        this.passwordError = this.password.length > 5 ? '' : "Password must be at least five characters long"
   }
}
}
</script>

<style>
form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    color: #555;
    border-bottom: 1px solid #ddd;
    
}
select{
 background: white;
}

input[type="checkbox"]{
    display: inline-block;
    width:16px;
    margin: 0 10px 0 0;
    position: relative;
    top:2px;
}
.pill{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
.submit{
    text-align: center;
}
button{
    background: #0b6dff;
    border: 0;
    padding:10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
    cursor: pointer;
}
.error{
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}
</style>