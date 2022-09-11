<script lang="ts" setup>
let loginLoading = ref(false)

definePageMeta({
  layout: "form-focus",
});

const loginForm = reactive({
  email:"",
  password:""
})

async function handleLogin(){
  try{
    loginLoading.value = true
    console.log("login button was hit",loginForm)
  }
  catch(e){
    alert("Error logging into the site check for username and password")
  }
  finally{
    loginLoading.value = false
  }
}
</script>

<template>
  <div>
    <h2 class="card-title mb-5 ml-2">Login</h2>
    <FormKit 
    type="form"
    submit-label="Login"
    @submit="handleLogin"
    v-model="loginForm"
    >
      <FormKit 
      name="email"
      label="Email address"
      validation="required|email"
      />

      <FormKit 
      type="password"
      label="password"
      name="password"
      validation="required"
      />
    </FormKit>
  </div>
</template>

<style scoped></style>
