<template>
  <div class="container">
    <form @submit.prevent="handleSubmit">
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Email address</label>
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
          v-model="email"
        />
      </div>
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">Password</label>
        <input
          type="password"
          class="form-control"
          id="exampleInputPassword1"
          v-model="password"
        />
      <p class="text-danger small">{{passwordError}}</p>
      </div>
      
      <div class="mb-3">
        <select
          v-model="role"
          style="width:50%; padding:10px; 20px; border-width:2px; border-radius:10px;"
        >
          <option value="Web Develper">Web Develper</option>
          <option value="Backend Develper">Backend Develper</option>
        </select>
      </div>


<div class="mb-3 form-check">
    <input type="checkbox" class="form-check-input" id="exampleCheck1" >
    <label class="form-check-label" for="exampleCheck1">Accept Terms and condition</label>
  </div>

      

      <label class="form-check-label" for="exampleCheck1">Language:</label>
      <div class="form-check">
        <input
          class="form-check-input"
          type="checkbox"
          value="English"
          v-model="languages"
        />
        <label class="form-check-label" for="flexCheckDefault"> English </label>
      </div>
      <div class="form-check">
        <input
          class="form-check-input"
          type="checkbox"
          value="Nepali"
          checked
          v-model="languages"
        />
        <label class="form-check-label" for="flexCheckChecked"> Nepali </label>
      </div>

      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">Skills</label>
        <input
          type="text"
          class="form-control"
          id="exampleInputPassword1"
          @keyup="addSkill"
          v-model="tempSkill"
        />
        <div style="display: flex">
          <div v-for="skill in skills" :key="skill" style="margin: 5px 4px 4px 0px;">
            <span class="badge text-bg-secondary" style="font-size: 14px; cursor:pointer;" @click="removeSkill(skill)">{{ skill }}</span>
          </div>
        </div>
      </div>

      <button  class="btn btn-outline-secondary">Submit</button>
    </form>
  </div>
  <p>Terms {{ terms }}</p>

  <p>{{ tempSkill }}</p>
  <p>{{ lang }}</p>
  
</template>

<script>
export default {
  name: "SignupForm",
  data() {
    return {
      email: "",
      password: "",
      role: "Web Develper",
      terms: true,
      languages: [],
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      console.log("function called");
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.tempSkill = this.tempSkill.substring(
            0,
            this.tempSkill.length - 1
          );
          this.skills.push(this.tempSkill);
          console.log(this.skills);
        }
        this.tempSkill = "";
      }
    },
    removeSkill(skillToBeRemoved) {
       this.skills= this.skills.filter((skill)=>skill!==skillToBeRemoved);
    },
    handleSubmit(){
        console.log('Form submitted');
        this.passwordError = this.password.length <5 || this.password.length === 0 ?'Password must be at least 5 characters':'';

        if(!this.passwordError){
            console.log(this.email);
            console.log(this.password);
            console.log(this.role);
            console.log(this.terms);
            console.log(this.languages);
            console.log(this.skills);


        }
    }
  },
};
</script>

<style>
.container {
  width: 50%;
  padding: 20px 40px;
  background: rgb(230, 228, 228);
}
</style>