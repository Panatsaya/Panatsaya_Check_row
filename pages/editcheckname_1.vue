<template>
  <v-container>
    <v-row justify="center">
      <!--ส่วนของ header!-->
      <v-app-bar
        class="head"
        fixed
        color="#141E61"
        height="90%"
      >
        <v-toolbar-title class="text-center">
          <h5>ระบบเช็คกิจกรรมเข้าแถวหน้าเสาธง</h5>
        </v-toolbar-title>
      </v-app-bar>
    </v-row>

    <!--ส่วนของ body!-->
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6" />
      <div class="bg">
        <br>
        <br>
        <br>
        <div>
          <v-icon
            large
            color="#141E61"
          >
            fas fa-edit
          </v-icon>
        </div>
        <div class="text1">
          <h2>แก้ไขเช็คชื่อเข้าแถวหน้าเสาธง</h2>
        </div>
        <br>
        <v-container>
          <div class="text">
            <v-btn
              color="grey"
              dark
              large
            >
              วันที่
              <v-menu
                ref="menu"
                v-model="menu"
                :close-on-content-click="false"
                :return-value.sync="date"
                transition="scale-transition"
                offset-y
                min-width="auto"
              >
                <template #activator="{ on, attrs }">
                  <v-text-field
                    v-model="date"
                    label=""
                    prepend-icon="mdi-calendar"
                    readonly
                    v-bind="attrs"
                    v-on="on"
                  />
                </template>
                <v-date-picker
                  v-model="date"
                  no-title
                  scrollable
                >
                  <v-spacer />
                  <v-btn
                    text
                    color="primary"
                    @click="menu = false"
                  >
                    Cancel
                  </v-btn>
                  <v-btn
                    text
                    color="primary"
                    @click="$refs.menu.save(date)"
                  >
                    OK
                  </v-btn>
                </v-date-picker>
              </v-menu>
              <v-spacer />
            </v-btn>
          </div>
          <v-container fluid>
            <v-row align="center">
              <v-col
                class="d-flex"
                cols="12"
                sm="6"
              >
                <v-select
                  :items="items"
                  label="ห้องเรียน"
                  outlined
                  light
                />
              </v-col>
            </v-row>
          </v-container>
          <v-btn
            class="btn1"
            depressed
            @click="onSave"
          >
            ค้นหา
          </v-btn>
        </v-container>

        <!--ส่วนของ footer!-->
        <div class="foot">
          <v-bottom-navigation
            :value="value"
            color="#FFEBC9"
            horizontal
            fixed
            background-color="#141E61"
          >
            <v-btn>
              <span />
              <v-icon />
            </v-btn>

            <v-btn>
              <span />
              <v-icon />
            </v-btn>
          </v-bottom-navigation>
        </div>
      </div>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    items: ['E1', 'E5']
  })
}
</script>

<style>
.bg {
   height: 88ex;
}
h5 {
  margin-left: 2ex;
}
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
.btn1 {
  margin-left: 5ex;
}
.txt1 {
  color: #27272c !important;
}
.v-text-field{
    border-radius: 15px;
}
.text1{
margin-top: 1rem;
  padding-left: 3px;
  color: #141E61;
}
</style>
