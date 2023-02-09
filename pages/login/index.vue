<template>
  <v-container>
    <v-row align-content="center" class="h-screen">
      <v-col align-self="center" justify="center">
        <v-sheet max-width="500px" class="ma-auto" rounded>
          <v-img
            src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
            height="200px"
            cover
          ></v-img>
          <v-form v-model="valid" class="py-8">
            <v-container>
              <v-row>

                <v-col
                  cols="12"
                >
                  <v-text-field
                    v-model="email"
                    :rules="[rules.emailMatch]"
                    label="E-mail"
                    required
                  ></v-text-field>
                </v-col>

                <v-col
                  cols="12"
                >
                  <v-text-field
                    v-model="password"
                    :append-inner-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                    :rules="[rules.required, rules.min]"
                    :type="show1 ? 'text' : 'password'"
                    name="input-10-1"
                    label="Password"
                    hint="At least 8 characters"
                    counter
                    @click:appendInner="show1 = !show1"
                  ></v-text-field>
                </v-col>

                <v-col>
                  <v-btn block class="bg-blue-darken-3">Login</v-btn>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
  definePageMeta({
    layout: "empty"
  });
  export default {
    data: () => ({
      valid: false,
      show1: false,
      show2: true,
      rules: {
        required: (value:string) => !!value || 'Required.',
        min: (v:string) => v.length >= 8 || 'Min 8 characters',
        emailMatch: () => (`The email and password you entered don't match`),
      },
      password: '',
      passwordRules: [
        (value:string) => {
          if (value) return true

          return 'Password is requred.'
        },
        (value:string) => {
          if (value?.length >= 6) return true

          return 'Password minimal character is 6 '
        },
      ],
      email: '',
      emailRules: [
        (value:string) => {
          if (value) return true

          return 'E-mail is requred.'
        },
        (value:string) => {
          if (/.+@.+\..+/.test(value)) return true

          return 'E-mail must be valid.'
        },
      ],
    }),
    
  }
</script>