<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <div class="bg" />
      <div class="pa-7">
        <center><v-img src="/logo.PNG" width="200" height="200" /></center>
      </div>
      <br>
      <div class="text">
        <v-form>
          <v-text-field
            label="ชื่อ-นามสกุล"
            single-line
            solo
            light
          />
          <v-text-field
            label="รหัสผ่าน"
            single-line
            solo
            light
          />
        </v-form>
      </div>
      <v-btn
        class="btn1"
        depressed
        @click="onSave"
      >
        LOG IN
      </v-btn>

      <div class="text-center">
        <v-dialog
          v-model="dialog"
          width="500"
        >
          <template #activator="{ on, attrs }">
            <v-btn
              color="blue lighten-2"
              dark
              v-bind="attrs"
              v-on="on"
            >
              LOG IN
            </v-btn>
          </template>

          <v-card>
            <v-card-title class="text-h5 grey lighten-2">
              Status Login
            </v-card-title>

            <v-card-text>
              SUCCESS LOGIN
            </v-card-text>

            <v-divider />

            <v-card-actions>
              <v-spacer />
              <v-btn
                color="primary"
                text
                @click="dialog = false"
              >
                I accept
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>
      <div class="text-center">
        <v-dialog
          v-model="dialog_false"
          width="500"
        >
          <v-card>
            <v-card-title class="text-h5 grey lighten-2">
              Status Login
            </v-card-title>

            <v-card-text>
              ERROR LOGIN
            </v-card-text>

            <v-divider />

            <v-card-actions>
              <v-spacer />
              <v-btn
                color="primary"
                text
                @click="dialog_false = false"
              >
                I accept
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default ({
  data: () => ({
    user: '',
    passwd: '',
    dialog: false,
    dialog_false: false
  }),
  methods: {
    async onSave () {
      console.log('onSave')
      const res = await fetch('http://localhost:7001/list?user=' +
      this.user + '&pass=' + this.passwd)
      const result = await res.json()
      console.log('data=', result)
      if (result.status > 0) {
        console.log('Login ok')
        this.dialog = true
        setInterval(() => {
          this.dialog_false = false
        }, 3000)
      } else {
        console.log('Error Login')
        this.dialog_false = true
        setInterval(() => {
          this.dialog_false = false
          this.$router.push('/login')
        }, 3000)
      }
    }

  }
})
</script>

<style>
/* .bgs {
  background-color: #e5eefa;
  height: 100%;
} */
h4 {
   color:#27272c;
   /* margin-top: 50px; */
}
.pa-7{
    margin-top: 1rem;
}
.text {
  margin-top: -15px;
  margin: 10px;
  padding-left: 3px;
  text-align: left;
}
.v-btn {
  background: #141E61 !important;;
  margin-bottom: 60px;
  margin: 2rem;
  margin-left: 2rem;
  size: 30px;
}
.txt1 {
  color: #27272c !important;
}
.v-text-field{
    border-radius: 15px;
}
</style>
