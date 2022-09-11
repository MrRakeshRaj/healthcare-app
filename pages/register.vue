<script lang="ts" setup>

const router = useRouter();

definePageMeta({
  layout : "form-focus"
})
let registerLoading = ref(true)

const registerForm = reactive({
  email:"",
  password:"",
  password_confirm:""
})

async function handleRegister(){
  try{
    registerLoading.value = true
    console.log("register button was hit",registerForm)
    router.push({path: "/login"})
  }
  catch(e){
    alert("Error registering, please contact support")
  }
  finally{
    registerLoading.value = false
  }
}
</script>

<template>
  <div>
    <h2 class="card-title mb-5 ml-2">Register</h2>
    <FormKit 
    type="form"
    submit-label="Login"
    @submit="handleRegister"
    v-model="registerForm"
    >
      <FormKit
      type="email"
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

      <FormKit
      type="password"
      name="password_confirm"
      label="Confirm password"
      validation="required|confirm"
      validation-label="Password"
      />
    </FormKit>
  </div>
</template>

<style scoped></style>
