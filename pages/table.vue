<template>
  <div class="rounded-xl  text-center">
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
    <v-row>
      <v-col>
        <div class="btn1">
          <v-autocomplete
            v-model="value"
            :items="week"
            dense
            filled
            label="สัปดาห์ที่"
            solo
            light
            style="height:50px; width:100px;"
            background-color="#7d9ecaa6"
          />
        </div>
      </v-col>
      <v-col>
        <div class="calendar">
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
                light
                label="วัน/เดือน/ปี"
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
        </div>
      </v-col>
    </v-row>

    <div class="txt01">
      <v-responsive
        class="overflow-y-auto"
        max-height="470"
      >
        <!-- ---------------------------ตาราง-------------------------- -->
        <v-simple-table light>
          <thead>
            <tr>
              <th class="text-left">
                ที่
              </th>
              <th class="text-center">
                รายชื่อ
              </th>
              <th class="text-center">
                นามสกุล
              </th>
              <th class="text-center">
                สถานะ
              </th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="st in student"
              :key="st.id"
              class="text-left"
            >
              <td> {{ st.id }} </td>
              <td> {{ st.name }} </td>
              <td> {{ st.lname }} </td>
              <!-- --------------------คลิกมา-------------- -->
              <v-radio-group
                v-model="study"
                row
                solo
                dense
                filled
              >
                <td>
                  <v-radio
                    label="มา"
                    color="info"
                    value="1"
                    style="font-size: 12px;"
                  />
                </td>
                <!-- --------------------คลิกขาด-------------- -->
                <td>
                  <v-radio
                    label="ขาด"
                    color="red"
                    value="0"
                  />
                </td>
                <!-- --------------------คลิกลา-------------- -->
                <td>
                  <v-radio
                    label="ลา"
                    color="orange"
                    value="2"
                  />
                </td>
                <!-- --------------------คลิกสาย-------------- -->
                <td>
                  <v-radio
                    label="สาย"
                    color="primary"
                    value="3"
                  />
                </td>
              </v-radio-group>
            </tr>
          </tbody>
        </v-simple-table>
      </v-responsive>
      <!----ปุ่ม ถอดไป----->
      <div class="next">
        <v-btn
          class="next_bt"
          style="height:40px; width:100px;"
          color="#4ba56d"
        >
          <span class="per" style="color:#e6e6e6; font-size: 19px;">ถัดไป</span>
        </v-btn>
      </div>
      <!----------->
    </div>
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
</template>
<script>
export default {
  layout: 'ly_check',
  data () {
    return {
      student: [
        { id: '1', name: 'Teerapong', lname: ' Tejaluang' },
        { id: '2', name: 'Nareetat', lname: ' Kongsatree' },
        { id: '3', name: 'Atriwat', lname: ' Tawan' },
        { id: '4', name: 'Jeerawan', lname: ' Lalee' },
        { id: '5', name: 'Sunisa', lname: ' Madee' },
        { id: '6', name: 'Pantakan', lname: ' Manat' },
        { id: '7', name: 'Peerapon', lname: ' Ponsa' },
        { id: '8', name: 'Manita', lname: ' Maijan' },
        { id: '9', name: 'Supaporn', lname: ' A-santea' }
      ],
      items: [
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me' },
        { title: 'Click Me' }
      ],
      week: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'],
      value: null
    }
  },
  computed: {
    upperName () {
      return this.name.toUpperCase()
    }
  },
  created () {
    this.Show()
  },
  methods: {
    async Show () {
      console.log('show data')
      const res = await fetch('http://localhost:7001/lists')
      const data2 = await res.json()
      this.student = data2.datas
      console.log(data2.datas)
    },
    edit (rid) {
      console.log('rid=', rid)
      this.$router.push('edit_std?rid=' + rid)
    }
  }
}
</script>
<style>
.bg{
    background: #f6f2e0 ;
}
.txt01{
    color: black;
}
.rounded-xl{
    padding-top: 4rem;
}
.calendar{
  padding-top: -4rem;
  margin-left: -6rem;
}
.btn1{
  margin-left: 5px;
  margin-top: 8px;
}
.next{
  margin-top: 15px;
}
</style>
