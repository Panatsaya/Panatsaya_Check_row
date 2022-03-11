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
        <div class="text">
          <v-icon
            large
            color="#000B49"
          >
            mdi-content-paste
          </v-icon>
          <h2>รายงานการมาเรียน</h2>
        </div>
        <br>
        <br>
        <v-simple-table dense>
          <template #default>
            <thead>
              <tr>
                <th class="text-left">
                  ชื่อ-นามสกุล
                </th>
                <th class="text-left">
                  มา
                </th>
                <th class="text-left">
                  ลา
                </th>
                <th class="text-left">
                  สาย
                </th>
                <th class="text-left">
                  ขาด
                </th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="item in desserts"
                :key="item.name"
              >
                <td>{{ item.name }}</td>
                <td>{{ item.come }}</td>
                <td>{{ item.leave }}</td>
                <td>{{ item.late }}</td>
                <td>{{ item.tear }}</td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
        <div class="back">
          <v-btn
            href="main"
            class="btn2"
            dark
            left
          >
            <v-icon
              dark
              left
            >
              mdi-arrow-left
            </v-icon>Back
          </v-btn>
        </div>
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
  data () {
    return {
      desserts: [
      ]
    }
  }
}
</script>

<style>
.bg {
  height: 88ex;
}
h5 {
  margin-left: 2ex;
}
.text{
  color: #000B49;
}
.back{
  position: fixed;
  left: 0;
  bottom: 0;
  margin-bottom: 5rem;
  margin-left: 2rem;
}
.btn2 {
  background: #9B0000 !important;;
  size: 30px;
  border-radius: 15px;
  box-shadow: 2px 2px 2px #a5a5a5;
}
</style>
