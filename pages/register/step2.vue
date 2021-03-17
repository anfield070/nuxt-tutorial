<template>
  <div>
    <v-app-bar color="deep-purple accent-4" dense dark>
      <v-toolbar-title>Register</v-toolbar-title>
    </v-app-bar>

    <v-container class="pt-0 pb-0">
      <v-row>
        <v-col cols="12">
          <div class="mt-8 text-primary text-title text-center">
            Step 2 of 2
          </div>
        </v-col>

        <v-col cols="12">
          <p class="text-center text-main mb-0 mt-4">Tell us more a bit...</p>
        </v-col>

        <v-col cols="12" md="12">
          <v-form>
            <v-text-field
              v-model="form.email"
              dense
              label="Email"
              required
            ></v-text-field>

            <v-text-field
              v-model="form.phone"
              dense
              label="Phone"
              required
            ></v-text-field>

            <v-dialog
              ref="dialog"
              v-model="modal"
              :return-value.sync="date"
              persistent
              width="290px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="form.birthday"
                  label="Birthday"
                  prepend-icon="mdi-calendar"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                  class="set-Birthday"
                ></v-text-field>
              </template>
              <v-date-picker
                :max="new Date().toISOString().substr(0, 10)"
                v-model="date"
                scrollable
              >
                <v-spacer></v-spacer>
                <v-btn text color="primary" @click="modal = false">
                  Cancel
                </v-btn>
                <v-btn text color="primary" @click="$refs.dialog.save(date)">
                  OK
                </v-btn>
              </v-date-picker>
            </v-dialog>

            <p class="text-center text-main mb-0 mt-4">Work Profile</p>

            <v-text-field
              v-model="form.cpmpany"
              dense
              label="Cpmpany"
              required
            ></v-text-field>

            <v-text-field
              v-model="form.position"
              dense
              label="Position"
              required
            ></v-text-field>
          </v-form>
        </v-col>
      </v-row>

      <div class="text-center">
        <v-btn
          rounded
          color="primary"
          class="w-100 mt-11 my-btn"
          @click="register"
          dark
        >
          Register
        </v-btn>

        <div class="w-100 text-center my-btn text-primart" @click="back">
          Back
        </div>
      </div>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        email: "",
        phone: "",
        birthday: new Date().toISOString().substr(0, 10),
        company: "",
        position: ""
      },
      menu: false,
      modal: false,
      menu2: false
    };
  },
  methods: {
    back() {
      this.$router.push("/register");
    },
    register() {
      console.log("Register");
    }
  }
};
</script>

<style lang="scss" scoped>
.v-form {
  padding: 0 20px;
}

.set-Birthday {
  position: relative;
  ::v-deep .v-input__prepend-outer {
    position: absolute;
    right: 0;
  }
}
</style>
