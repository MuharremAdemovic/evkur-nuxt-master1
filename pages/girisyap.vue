<template>
  <section class="form-section">
    <div class="container">
      <div class="form login-form">
        <form
          action="/uye-girisi"
          method="post"
          class="validate"
          novalidate="novalidate"
        >
          <input
            name="__RequestVerificationToken"
            type="hidden"
            value="4xky5t8POaQTaa8NLL6wrw6y4Odofn-EfxkNkqarK_hRDWwdfK4mgeyexty6P2YmceurV8dW6-BXzjvVao48wBRDPj8wOdI-jJ7UfmToPAk1"
          />
          <Login />
          <Register />
          <input type="hidden" name="returnUrl" />
          <input type="hidden" name="showGuestButton" value="0" />
        </form>
      </div>
    </div>
  </section>
</template>

<script>
import Login from '@/components/Auth/Login'
import Register from '@/components/Auth/Register'

export default {
  components: { Register, Login },
  data: function () {
    return {
      isLogin: true,
    }
  },
  
  
}
</script>