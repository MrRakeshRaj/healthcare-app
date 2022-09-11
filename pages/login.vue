<script lang="ts" setup>
const loading = ref(false)

definePageMeta({
  layout: "form-focus",
});

const form = reactive({
  email:"",
  password:""
})

async function handleLogin(){
  try{
    loading.value = true
    console.log("login button was hit",form)
  }
  catch(e){
    alert("Error logging into the site check for username and password")
  }
  finally{
    loading.value = false
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
    v-model="form"
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
