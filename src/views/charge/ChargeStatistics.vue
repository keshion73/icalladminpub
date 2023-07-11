<template>
  <div>
    <PageTit />
    <!-- 기본 -->
    <div class="page-bg page-flex charge-stat01">
      <div class="sch-wrap d-flex">
        <div class="d-flex">
          <div>
            <div class="d-flex sch-input input-date">
              <div class="th">
                기간
              </div>
              <div class="td">
                <div class="d-flex align-center">
                  <div>
                    <v-menu v-model="menu" :close-on-content-click="false" transition="scale-transition" offset-y>
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field v-model="s_date" v-bind="attrs" outlined v-on="on"
                          prepend-inner-icon="fa-"></v-text-field>
                      </template>
                      <v-date-picker v-model="s_date" no-title @input="menu = false"></v-date-picker>
                    </v-menu>
                  </div>
                  <p style="margin:0 5px">~</p>
                  <div>
                    <v-menu v-model="menu2" :close-on-content-click="false" transition="scale-transition" offset-y>
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field v-model="e_date" v-bind="attrs" outlined v-on="on"
                          prepend-inner-icon="fa-" type="number"></v-text-field>
                      </template>
                      <v-date-picker v-model="e_date" no-title @input="menu2 = false"></v-date-picker>
                    </v-menu>
                  </div>
                </div>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                코드명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                대리점명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
          </div>          
        </div>
        <div>
          <v-btn class="btnbg">조회</v-btn>
        </div>
      </div>
      <div class="sch-table-wrap">
        <div>
          <v-data-table :headers="headers" :items="contents" :items-per-page="itemsPerPage" hide-default-footer
            :mobile-breakpoint="0" :class="$vuetify.breakpoint.xs?'mobile-table':''">
            <template v-slot:item="{ item }">
              <tr>
                <td class="bg">{{item.com}}</td>
                <td>{{item.num1}}</td>
                <td>{{item.num2}}</td>
                <td>{{item.num3}}</td>
                <td>{{item.num4}}</td>
                <td>{{item.num5}}</td>
                <td></td>
              </tr>
            </template>
          </v-data-table>
        </div>
      </div>
    </div>
    <!-- 충전통계_표가 두개, 조회부가 다를 경우 -->
    <!-- 표가 두개, 조회부가 동일할 경우 2번째 sch-wrap 주석처리 -->
    <!-- <div class="page-bg page-flex charge-stat02">
      <div class="sch-wrap d-flex">
        <div class="d-flex">
          <div>
            <div class="d-flex sch-input input-date">
              <div class="th">
                기간
              </div>
              <div class="td">
                <div class="d-flex align-center">
                  <div>
                    <v-menu v-model="menu" :close-on-content-click="false" transition="scale-transition" offset-y>
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field v-model="s_date" v-bind="attrs" outlined v-on="on"
                          prepend-inner-icon="fa-"></v-text-field>
                      </template>
                      <v-date-picker v-model="s_date" no-title @input="menu = false"></v-date-picker>
                    </v-menu>
                  </div>
                  <p style="margin:0 5px">~</p>
                  <div>
                    <v-menu v-model="menu2" :close-on-content-click="false" transition="scale-transition" offset-y>
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field v-model="e_date" v-bind="attrs" outlined v-on="on"
                          prepend-inner-icon="fa-" type="number"></v-text-field>
                      </template>
                      <v-date-picker v-model="e_date" no-title @input="menu2 = false"></v-date-picker>
                    </v-menu>
                  </div>
                </div>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                코드명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                대리점명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
          </div>          
        </div>
        <div>
          <v-btn class="btnbg">조회</v-btn>
        </div>
      </div>
      <div class="sch-table-wrap">
        <div>
          <v-data-table :headers="headers" :items="contents" :items-per-page="itemsPerPage" hide-default-footer
            :mobile-breakpoint="0" :class="$vuetify.breakpoint.xs?'mobile-table':''">
            <template v-slot:item="{ item }">
              <tr>
                <td>{{item.com}}</td>
                <td>{{item.num1}}</td>
                <td>{{item.num2}}</td>
                <td>{{item.num3}}</td>
                <td>{{item.num4}}</td>
                <td>{{item.num5}}</td>
                <td></td>
              </tr>
            </template>
          </v-data-table>
          <p class="read font-weight-bold">조회 <span style="color:#2F79E8">32</span></p>
          <v-pagination v-model="page" :length="15" :total-visible="7" circle active-color="#2F79E8"></v-pagination>
        </div>
      </div>
      <div class="sch-wrap d-flex" style="margin-top:16px;"> 
        <div class="d-flex">
          <div>
            <div class="d-flex sch-input input-date">
              <div class="th">
                기간
              </div>
              <div class="td">
                <div class="d-flex align-center">
                  <div>
                    <v-menu v-model="menu" :close-on-content-click="false" transition="scale-transition" offset-y>
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field v-model="s_date" v-bind="attrs" outlined v-on="on"
                          prepend-inner-icon="fa-"></v-text-field>
                      </template>
                      <v-date-picker v-model="s_date" no-title @input="menu = false"></v-date-picker>
                    </v-menu>
                  </div>
                  <p style="margin:0 5px">~</p>
                  <div>
                    <v-menu v-model="menu2" :close-on-content-click="false" transition="scale-transition" offset-y>
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field v-model="e_date" v-bind="attrs" outlined v-on="on"
                          prepend-inner-icon="fa-" type="number"></v-text-field>
                      </template>
                      <v-date-picker v-model="e_date" no-title @input="menu2 = false"></v-date-picker>
                    </v-menu>
                  </div>
                </div>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                코드명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                대리점명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
          </div>          
        </div>
        <div>
          <v-btn class="btnbg">조회</v-btn>
        </div>
      </div>
      <div class="sch-table-wrap">
        <div>
          <v-data-table :headers="headers" :items="contents" :items-per-page="itemsPerPage" hide-default-footer
            :mobile-breakpoint="0" :class="$vuetify.breakpoint.xs?'mobile-table':''">
            <template v-slot:item="{ item }">
              <tr>
                <td>{{item.com}}</td>
                <td>{{item.num1}}</td>
                <td>{{item.num2}}</td>
                <td>{{item.num3}}</td>
                <td>{{item.num4}}</td>
                <td>{{item.num5}}</td>
                <td></td>
              </tr>
            </template>
          </v-data-table>
          <p class="read font-weight-bold">조회 <span style="color:#2F79E8">32</span></p>
          <v-pagination v-model="page" :length="15" :total-visible="7" circle active-color="#2F79E8"></v-pagination>
        </div>
      </div>
    </div> -->
  </div>
</template>
<script>
  import PageTit from "@/components/PageTit.vue";
  export default {
    components: {
      PageTit
    },
    data() {
      return {
        page: 1,
        headers: [
          {
            text: '사업자',
            value: 'com',
            sortable: false,
            width: '8%'
          },
          {
            text: '충전건수',
            value: 'num1',
            sortable: false,
            width: '8%'
          },
          {
            text: '요금제',
            value: 'num2',
            sortable: false,
            width: '7%'
          },
          {
            text: '충전금액',
            value: 'num3',
            sortable: false,
            width: '7%'
          },
          {
            text: '할인금액',
            value: 'num4',
            sortable: false,
            width: '7%'
          },
          {
            text: '차액',
            value: 'num5',
            sortable: false,
            width: '7%'
          },         
          {
            text: '',
            sortable: false,
          },
        ],
        contents: [{
          com: '예자인',
          num1: '4',
          num2: '32,000',
          num3: '32,000',
          num4: '32,000',
          num5: '32,000',
        },
        {
          com: '디자인',
          num1: '4',
          num2: '32,000',
          num3: '32,000',
          num4: '32,000',
          num5: '32,000',
        },
        ]
      }
    },
    computed: {
      pageCount() {
        return Math.ceil(this.contents.length / this.itemsPerPage)
      },
    },
  }
</script>
<style lang="scss" scoped>
.sch-table-wrap{
  tbody td.bg{
    background: rgba(229, 30, 120, 0.1);
  }
}

  @include pc {
    .sch-table-wrap {
      .read{
            position: absolute;
    bottom: 20px;
    left: 24px;
      }
    }
  }
  .charge-stat01{
    background: none !important;
    .v-data-table {
        height: calc(100vh - 270px) !important;
      }
  }
  .charge-stat02{
    background: none !important;
    .v-data-table {
        height: 280px;
      }
  }

</style>