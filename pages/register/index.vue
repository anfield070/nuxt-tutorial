<template>
  <div>
    <v-app-bar color="deep-purple accent-4" dense dark>
      <v-toolbar-title>Register</v-toolbar-title>
    </v-app-bar>

    <v-container class="pt-0 pb-0">
      <v-row>
        <v-col cols="12">
          <div class="mt-8 text-primary text-title text-center">
            Step 1 of 2
          </div>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <div class="text-center">
            <img src="~/assets/images/profile.png" alt="" width="155" />
          </div>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <div class="text-center pt-2 pb-0">Display name</div>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12" md="6">
          <v-form>
            <v-text-field
              v-model="form.firstname"
              dense
              label="First name"
              required
            ></v-text-field>

            <v-text-field
              v-model="form.lastname"
              dense
              label="Last name"
              required
            ></v-text-field>

            <p>Gender</p>
            <v-radio-group v-model="form.gender" row>
              <v-radio label="Male" value="1"></v-radio>
              <v-radio label="Female" value="2"></v-radio>
            </v-radio-group>
          </v-form>
        </v-col>
      </v-row>

      <div class="text-center">
        <v-btn
          rounded
          color="primary"
          class="w-100 mt-11 my-btn"
          @click="next"
          dark
        >
          Next
        </v-btn>
      </div>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dialog: {
        isShow: false,
        title: "",
        message: ""
      },
      errormsg: "",
      form: {
        firstname: this.$store.getters.getRegister.firstname,
        lastname: this.$store.getters.getRegister.lastname,
        gender: this.$store.getters.getRegister.gender
      }
    };
  },
  methods: {
    validate() {
      let validated = true;
      const errors = [];
      let errormsg = "";
      const validatorField = ["firstname", "lastname", "gender"];
      validatorField.forEach(field => {
        if (this.form[field] === "") {
          validated = false;
          errors.push(`${field} can not be null`);
        }
      });

      if (!validated) {
        this.$store.dispatch("setDialog", {
          isShow: true,
          title: "Form is error",
          message: errors.map(error => error + "<br/>").join("")
        });
      }
      return validated;
    },
    next() {
      if (this.validate()) {
        this.$store.dispatch("setRegister", this.form);
        this.$router.push("/register/step2");
      }
    }
  }
};
</script>

<style scoped>
.v-form {
  padding: 0 20px;
}
</style>
