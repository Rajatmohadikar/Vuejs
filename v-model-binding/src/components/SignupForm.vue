<template>
   <form @submit.prevent="handleSubmit">
        <label>Email:</label>
        <input type="email" required v-model="email">

        <label>Password:</label>
        <input type="password" required v-model="password">
        <div v-if="passwordError" class="error">{{ passwordError }}</div>

        <label>Role:</label>
        <select v-model="role">
            <option value="developer">Web Developer</option>
            <option value="designer">Web Designer</option>
        </select>

        <label>Skills:</label>
        <input type="text" v-model="tempSkill" @keyup="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill">
            <span @click="deleteSkill(skill)">{{ skill }}</span>
        </div>

        <div class="terms">
            <label>Accpet Terms & Conditions:</label>
            <input type="checkbox" v-model="terms" required>
        </div>

        <div class="submit">
            <button>Create an account</button>
        </div>

        <!-- <div>
            <input type="checkbox" value="rajat" v-model="names">
            <label>Rajat</label>
        </div>
        <div>
            <input type="checkbox" value="ram" v-model="names">
            <label>Ram</label>
        </div>
        <div>
            <input type="checkbox" value="shyam" v-model="names">
            <label>shyam</label>
        </div> -->






   </form>

   <p>Email: {{ email }}</p>
   <p>Password: {{ password }}</p>
   <p>Role: {{ role }}</p>
   <p>Terms accepted: {{ terms }}</p>
   <!-- <p>Names: {{ names }}</p> -->
</template>

<script>
export default{
    data(){
        return{
            email: '',
            password: '',
            role:'designer',
            terms: false,
            // names: []
            tempSkill: '',
            skills:[],
            passwordError: ''
        }
    },
    methods: {
        addSkill(e){
            if (e.key ===',' && this.tempSkill) {
                if (!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)  
                }
                this.tempSkill=''
            }
        },
        deleteSkill(skill){
            this.skills=this.skills.filter((item) => {
                return skill !==item
            })
        },
        handleSubmit(){
            //validate password
            this.passwordError = this.password.length > 5 ? '' 
             : 'Password must be 6 char long'

             if (!this.passwordError) {
                console.log('email: ', this.email)
                console.log('password: ', this.password)
                console.log('role: ', this.role)
                console.log('skills: ', this.skills)
                console.log('terms accepted: ', this.terms)
             }
        }
    }
}

</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #B4886B;
  display: inline;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input, select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid chocolate;
  color: #555;
}
button{
    background: blue;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: wheat;
    border-radius: 20px;
}
.submit{
    text-align: center;
}

</style>