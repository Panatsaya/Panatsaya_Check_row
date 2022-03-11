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
          <v-icon large>
            fas fa-edit
          </v-icon>
        </div>
        <div>
          <h2>แก้ไขเช็คชื่อเข้าแถวหน้าเสาธง</h2>
        </div>
        <br>
        <v-container fluid>
          <v-radio-group
            row
          >
            <v-radio
              label="มา"
              value="radio-1"
            />
            <v-radio
              label="ลา"
              value="radio-2"
            />
            <v-radio
              label="ขาด"
              value="radio-3"
            />
            <v-radio
              label="สาย"
              value="radio-4"
            />
          </v-radio-group>
        </v-container>
        <br>
        <v-btn
          color="#141E61"
          class="btn1"
          depressed
        >
          บันทึก
        </v-btn>
      </div>
    </v-row>

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
</style>
