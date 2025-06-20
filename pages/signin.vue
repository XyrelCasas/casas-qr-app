<template>
  <div class="d-flex justify-center align-center" style="height: 100vh;">
  <v-container>
    <v-row justify="center">
      <v-col cols="12" sm="8" md="4">
        <v-card>
          <v-card-title class="text-h5">Login</v-card-title>
          <v-card-text>
            <v-form>
              
              <v-text-field
                label="Email"
                type="email"
                required
              prepend-inner-icon="mdi-email"></v-text-field>

             
              <v-text-field
                label="Password"
                type="password"
                required
             prepend-inner-icon="mdi-lock" ></v-text-field>

              
              <v-btn color="green" small>Log In</v-btn>
               <v-btn color="red" small>Sign in with Google</v-btn>
            </v-form>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
  </div>
</template>

<script>

export default{
layout:"auth",
}
</script>

<style scoped>
.v-card {
  max-width: 500px;
  margin: auto;
}
</style>
