<template>
  <form @submit.prevent="handleSubmit">
      <label>Email</label>
      <input type="email" required v-model="email">

      <label>Password</label>
      <input type="password" required v-model="password">
      <div class="error" v-if="passwordError">{{passwordError}}</div>

      <label>Position</label>
      <select v-model="position">
          <option value="developer">Web developer</option>
          <option value="designer">Web designer</option>
          <option value="system">System Ad</option>
      </select>

      <label>Skills</label>
      <input type="text" v-model="tempSkill" @keydown.enter='addSkill'>
      <div v-for="skill in skills" :key="skill" class="pill">
          <span @click="deleteSkill(skill)">{{skill}}</span>
      </div>

    <div class="terms">
        <input type="checkbox" v-model="terms" required>
        <label>Accept conditions</label>
    </div>
    <div class="submit">
        <button>Submit</button>
    </div>
  </form>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            position:'',
            terms: false,
            tempSkill: '',
            skills: [],
            passwordError: ''
        }
    },
    methods: {
        addSkill(event){
            event.preventDefault();
            var val = event.target.value.trim()
            if (val.length > 0){
                this.skills.push(val)
                this.tempSkill = ''
            }
        },
        
        deleteSkill(skill){
            this.skills = this.skills.filter((item)=>{
                return skill !== item
            })
        },
        handleSubmit(){
            this.passwordError = this.password.length > 5 ? '' : 'Password at least 6 must be'
        },
    },

    
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
        color: rgb(231, 3, 3);
        display: inline-block;
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
        border-bottom: 1px solid #ddd;
        color: #555;
    }

    input[type="checkbox"]{
        display: inline-block;
        width: 16px;
        margin: 0 10px 0 0;
        position: relative;
        top: 2px;
    }
    .pill {
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

    button{
        background: #0b6dff;
        border: 0;
        padding: 10px 20px;
        margin-top: 20px;
        color: white;
        border-radius: 20px;
    }

    .submit{
        text-align: center;
    }

    .error{
        color: #ff0062;
        margin-top: 10px;
        font-size: 0.8em;
        font-weight: bold;
    }
</style>