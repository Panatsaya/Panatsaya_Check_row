<template>
  <v-container>
    <v-row justify="center">
      <div class="bg">
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

        <!--ส่วนของ body!-->
        <v-row justify="start">
          <div class="top">
            <v-icon
              size="48px"
              color="#495371"
            >
              home
            </v-icon><h2>หน้าหลัก</h2>
          </div>
          <div class="menu">
            <v-btn
              color="#C4C4C4"
              dark
              large
              href="editcheckname_1"
            >
              <v-icon
                dark
                left
              >
                fas fa-edit
              </v-icon>
              แก้ไขเช็คชื่อเข้าแถวหน้าเสาธง
            </v-btn>
          </div>
          <div class="my-2">
            <v-btn
              color="#C4C4C4"
              dark
              large
              href="show"
            >
              <v-icon
                dark
                left
              >
                mdi-content-paste
              </v-icon>
              สรุปผลรายงานการเข้าแถว
            </v-btn>
          </div>
          <div class="my-2">
            <v-btn
              color="#C4C4C4"
              dark
              large
              href="show_2"
            >
              <v-icon
                dark
                left
              >
                mdi-chart-bar
              </v-icon>
              รายงานการมาเรียน
              <v-menu
                left
                bottom
              >
                <template #activator="{ on, attrs }">
                  <v-btn
                    icon
                    v-bind="attrs"
                    v-on="on"
                  >
                    <v-icon>mdi-dots-vertical</v-icon>
                  </v-btn>
                </template>

                <v-list>
                  <v-list-item
                    v-for="n in 5"
                    :key="n"
                    @click="() => {}"
                  >
                    <v-list-item-title>E {{ n }}</v-list-item-title>
                  </v-list-item>
                </v-list>
              </v-menu>
            </v-btn>
          </div>
          <div class="my-2">
            <v-btn
              color="#C4C4C4"
              dark
              large
              href="information"
            >
              <v-icon
                dark
                left
              >
                mdi-clipboard-text
              </v-icon>
              บันทึกพฤติกรรม/ดูข้อมูลนักเรียน
              <v-menu
                left
                bottom
              >
                <template #activator="{ on, attrs }">
                  <v-btn
                    icon
                    v-bind="attrs"
                    v-on="on"
                  >
                    <v-icon>mdi-dots-vertical</v-icon>
                  </v-btn>
                </template>

                <v-list>
                  <v-list-item
                    v-for="n in 5"
                    :key="n"
                    @click="() => {}"
                  >
                    <v-list-item-title>E {{ n }}</v-list-item-title>
                  </v-list-item>
                </v-list>
              </v-menu>
            </v-btn>
          </div>
        </v-row>
        <!--ส่วนของ foot!-->
        <v-bottom-navigation
          :value="value"
          color="#F5F5F5"
          background-color="#2D4263"
          grow
          light
          absolute
        >
          <v-btn href="main">
            <span>Home</span>

            <v-icon>
              home
            </v-icon>
          </v-btn>
        </v-bottom-navigation>
      </div>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data: () => ({ value: 1 })
}
</script>
<style>
.bg{
    background-color: #F5F5F5;
    height: 100%;
}
.menu{
  margin-top: 2rem;
  margin-left: 3rem;
}
.my-2{
  margin-left: 3rem;
}
.top{
  margin-left: 10rem;
  color: #495371;
  margin-top: 7rem;
}
</style>
