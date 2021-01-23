<template>
  <section class="form-section">
    <div class="container">
      <div class="form register-form">
        <form
          @submit="register"
          action="/uye-ol"
          method="post"
          class="validate"
          novalidate="novalidate"
        >
          <input
            name="__RequestVerificationToken"
            type="hidden"
            value="PsQOMc2Cn4mdkApiZnjvVBTI3dEQYunoTDR51Ep33BKPGNf-v7EAen3TDxWet38derO-X6qYZRK5736D30d7kT0ob_jmpwwnIWJqK1g9y1k1"
          />
          <div class="form-title">Yeni Üyelik Oluşturma</div>
          <div class="form-subtitle">Kişisel Bilgileriniz</div>
          <div class="form-item-container">
            <div class="col-2">
              <div class="form-item">
                <label> <span>*</span> E-posta </label>
                <input
                  class="validate-item email"
                  data-error="Lütfen geçerli bir e-posta adresi giriniz."
                  id="Email"
                  name="Email"
                  type="text"
                  value=""
                  v-model="form.email"
                />
              </div>
            </div>
            <div class="col-2">
              <div class="form-item password-hide">
                <label> <span>*</span> Şifre </label>
                <input
                  class="validate-item password"
                  data-error="Bu alan zorunludur."
                  id="Password"
                  minlengthattr="6"
                  name="Password"
                  :type="showPassword ? 'text' : 'password'"
                  v-model="form.password"
                />
                <span class="password-hint"></span>
              </div>
            </div>

            <div class="col-2"></div>
            <div class="col-2"></div>
          </div>

          <div class="form-item form-item-button form-item-button-with-border">
            <div class="aggrements form-mini-checkbox">
              <div class="form-item">
                <input
                  class="validate-item"
                  data-val="true"
                  data-val-required="AcceptUserAggrement alanı gereklidir."
                  id="AcceptUserAggrement"
                  name="AcceptUserAggrement"
                  type="checkbox"
                  value="true"
                /><input
                  name="AcceptUserAggrement"
                  type="hidden"
                  value="false"
                />
                <label for="AcceptUserAggrement"
                  ><a href="javascript:void(0)">Üyelik sözleşmesi</a>ni okudum
                  ve kabul ediyorum.</label
                >
              </div>
              <div class="form-item">
                <input
                  checked="checked"
                  data-val="true"
                  data-val-required="AllowCommunicationSms alanı gereklidir."
                  id="AllowCommunicationSms"
                  name="AllowCommunicationSms"
                  type="checkbox"
                  value="true"
                /><input
                  name="AllowCommunicationSms"
                  type="hidden"
                  value="false"
                />
                <label for="AllowCommunicationSms"
                  >SMS ile iletişime izin veriyorum.</label
                >
              </div>
              <div class="form-item">
                <input
                  checked="checked"
                  data-val="true"
                  data-val-required="AllowCommunicationEmail alanı gereklidir."
                  id="AllowCommunicationEmail"
                  name="AllowCommunicationEmail"
                  type="checkbox"
                  value="true"
                /><input
                  name="AllowCommunicationEmail"
                  type="hidden"
                  value="false"
                />
                <label for="AllowCommunicationEmail"
                  >E-posta ile iletişime izin veriyorum.</label
                >
              </div>
            </div>
            <a @click="register" class="button red submit-button">
              <span> ÜYE OL </span>
            </a>
          </div>
        </form>
      </div>
    </div>
  </section>
</template>

<script>

import firebase from 'firebase/app'
import 'firebase/auth'

export default {
  name: "Register",
  data: () => {
    return {
      form: {  
        email: "",
        password: "",
        errors: ""  
      },
      showPassword: false,
    };
  },
  methods: {
    register(e) {
      e.preventDefault();
      this.$fire.auth.createUserWithEmailAndPassword(this.$data.email,this.$data.password).then(user => {
        console.log(user);
        this.$router.push('components/Evkur')
      }).catch(error => {
        this.error = error;
      })
    },
  },
};
</script>
