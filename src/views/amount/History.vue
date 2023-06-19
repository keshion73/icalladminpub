<template>
  <div>
    <PageTit />
    <div class="page-bg page-flex">
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
                        <!-- YY-MM-DD형식 -->
                        <v-text-field v-model="s_date" v-bind="attrs" outlined v-on="on" hide-details="auto"
                          prepend-inner-icon="fa-"></v-text-field>
                      </template>
                      <v-date-picker v-model="s_date" no-title @input="menu = false"></v-date-picker>
                    </v-menu>
                  </div>
                  <p style="margin:0 5px">~</p>
                  <div>
                    <v-menu v-model="menu2" :close-on-content-click="false" transition="scale-transition" offset-y>
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field v-model="e_date" v-bind="attrs" outlined v-on="on" hide-details="auto"
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
                <td>{{item.code}}</td>
                <td>{{item.com}}</td>
                <td>{{item.num1}}</td>
                <td>{{item.num2}}</td>
                <td>{{item.num3}}</td>
                <td>{{item.num4}}</td>
                <td>{{item.num5}}</td>
                <td>{{item.num6}}</td>
                <td>{{item.num7}}</td>
                <td></td>
              </tr>
            </template>
          </v-data-table>
          <p class="read font-weight-bold">조회 <span style="color:#2F79E8">32</span></p>
          <v-pagination v-model="page" :length="15" :total-visible="7" circle active-color="#2F79E8"></v-pagination>
        </div>
      </div>
    </div>
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
        headers: [{
            text: '대리점 코드',
            value: 'code',
            sortable: false,
            width: '8%'
          },
          {
            text: '대리점명',
            value: 'com',
            sortable: false,
            width: '10%'
          },
          {
            text: '연동결과',
            value: 'num1',
            sortable: false,
            width: '8%'
          },
          {
            text: '거래날짜',
            value: 'num2',
            sortable: false,
            width: '13%'
          },
          {
            text: '금액',
            value: 'num3',
            sortable: false,
            width: '8%'
          },
          {
            text: '은행명',
            value: 'num4',
            sortable: false,
            width: '8%'
          },
          {
            text: '계좌번호',
            value: 'num5',
            sortable: false,
            width: '10%'
          },
          {
            text: '입금자명',
            value: 'num6',
            sortable: false,
            width: '8%'
          },
          {
            text: '거래번호',
            value: 'num7',
            width: '10%'
          },
          {
            text: '',
            sortable: false,
          },
        ],
        contents: [{
          code: 'IC290003',
          com: 'MOBILAND',
          num1: '성공',
          num2: '2023-03-03  16:07:23',
          num3: '32,000',
          num4: '카카오뱅크',
          num5: '013-7754-8808-01',
          num6: '예자인',
          num7: '010-7754-8808'
        }, ]
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
  ::v-deep {
    .v-data-table__wrapper {
      tbody td:first-child {
        text-decoration: underline;
      }
    }
  }

  @include pc {
    .sch-table-wrap {
      .read{
            position: absolute;
    bottom: 20px;
    left: 24px;
      }
      .v-data-table {
        height: calc(100vh - 330px);
      }
    }
  }

</style>