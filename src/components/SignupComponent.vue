<template>
  <form class="description" @submit.prevent="submit">
    <h4 class="text-center createBtn mb-4 py-2">Sign Up Form</h4>
    <!-- Email -->
    <div class="form-group">
      <label for="exampleInputEmail1">Email address</label>
      <input type="email" class="form-control inputColor my-2" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email" v-model="email">
    </div>

    <!-- Password -->
    <div class="form-group">
      <label class="mt-3" for="exampleInputPassword1">Password</label>
      <input type="password" class="form-control inputColor my-2" id="exampleInputPassword1" placeholder="Password" v-model="password">
      <div v-if="errMsg">
        <div class="form-text errMsgColor">{{ errMsg }}</div>
      </div>
    </div>

    <!-- Role -->
    <label class="mt-3">Role</label>
    <select class="form-select inputColor optionTextColor my-2">
      <option>Select your role</option>
      <option value="frontend">Frontend Developer</option>
      <option value="backend">Backend Developer</option>
    </select>

    <!-- Multiple Checkbox -->
    <div class="">
      <label class="mt-3">Choose Frameworks</label>

      <div class="optionTextColor">
        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="react" id="flexCheckReact" v-model="frameworks">
          <label class="form-check-label" for="flexCheckReact">React</label>
        </div>

        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="vue" id="flexCheckVue" v-model="frameworks">
          <label class="form-check-label" for="flexCheckVue">Vue</label>
        </div>

        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="angular" id="flexCheckAngular" v-model="frameworks">
          <label class="form-check-label" for="flexCheckAngular">Angular</label>
        </div>

        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="node" id="flexCheckNode" v-model="frameworks">
          <label class="form-check-label" for="flexCheckNode">Node</label>
        </div>
      </div>

    </div>

    <!-- Other Skills -->
    <div class="form-group">
      <label class="mt-3" for="otherSkillset">Other Skills</label>
      <input type="email" class="form-control inputColor my-2" id="otherSkillset" placeholder="Other Skills" v-model="skill" @keyup="addKey">
      <div v-for="otherSkill in otherSkills" :key="otherSkill">
        <p>{{ otherSkill }}
          <span class="deleteBtn" @click="deleteSkill(otherSkill)">&#10060;</span>
        </p>
      </div>
    </div>

    <!-- Accept Terms and Conditions -->
    <div class="form-check mt-3">
      <input type="checkbox" class="form-check-input" id="acceptTermsConditions" v-model="acceptBtn">
      <label class="form-check-label" for="acceptTermsConditions">Accept Terms and Conditions</label>
    </div>

    <button type="submit" class="btn createBtn mt-2">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: [],
      frameworks: [],
      otherSkills: [],
      skill: '',
      acceptBtn: false,
      errMsg: ''
    }
  },
  methods: {
    addKey(event) {
      if (event.key === ' ' && this.skill) {
        this.otherSkills.push(this.skill);
        this.skill = '';
      }
    },
    deleteSkill(otherSkill) {
      this.otherSkills = this.otherSkills.filter(loopedSkill => {
        return loopedSkill !== otherSkill;
      })
    },
    submit() {
      if (this.password.length < 8) {
        return this.errMsg = 'Password must be at least 8 characters.';
      } else {
        this.errMsg = '';
      }
      this.password = '';
    }
  }
}
</script>

<style>
  .description {
    font-family: 'Fira Code', monospace;
    font-size: 18px;
  }
  form {
    max-width: 400px;
    margin: 50px auto;
    padding: 30px;
    text-align: left;
    background-color: #2e3440;
    border-radius: 10px;
    color: #d8dee9;
  }
  .inputColor {
    background-color: hsl(218, 17%, 12%);
    color:#d8dee9
  }
  .optionTextColor {
    color: #d8dee9;
  }
  .deleteBtn {
    font-size: 10px;
    cursor: pointer;
  }
  .errMsgColor {
    color: red;
    font-size: 13px;
  }
  .createBtn {
    background-color: #d8dee9;
    color: #2e3440;
  }
</style>