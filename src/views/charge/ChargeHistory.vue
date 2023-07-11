<template>
  <div>
    <PageTit />
    <div class="page-bg page-flex">
      <v-tabs v-model="tab" height="50px" hideSlider bg-color="primary">
            <v-tab>스마텔</v-tab>
            <v-tab>파워콜</v-tab>
          </v-tabs>
          <v-window v-model="tab">
            <v-window-item :transition="false">
              <div>
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
          <div>
            <div class="d-flex sch-input">
              <div class="th">
                충전번호
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
                <td>{{item.no}}</td>
                <td>{{item.num}}</td>
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
            </v-window-item>
            <v-window-item :transition="false">
              <div>
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
          <div>
            <div class="d-flex sch-input">
              <div class="th">
                충전번호
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
                <td>{{item.no}}</td>
                <td>{{item.num}}</td>
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
            </v-window-item>
          </v-window>      
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
        tab: null,
        page: 1,
        headers: [{
            text: '순번',
            value: 'no',
            sortable: false,
            width: '5%'
          },
          {
            text: '충전번호',
            value: 'num',
            sortable: false,
            width: '8%'
          },
          {
            text: '대리점코드',
            value: 'code',
            sortable: false,
            width: '8%'
          },
          {
            text: '대리점명',
            value: 'com',
            sortable: false,
            width: '8%'
          },
          {
            text: '담당자',
            value: 'num2',
            sortable: false,
            width: '5%'
          },
          {
            text: '전화번호',
            value: 'num3',
            sortable: false,
            width: '10%'
          },
          {
            text: '요금제',
            value: 'num4',
            sortable: false,
            width: '7%'
          },
          {
            text: '충전금액',
            value: 'num5',
            sortable: false,
            width: '7%'
          },
          {
            text: '할인금액',
            value: 'num6',
            sortable: false,
            width: '7%'
          },
          {
            text: '충전일',
            value: 'num7',
            width: '12%'
          },
          {
            text: '충전결과',
            value: 'num8',
            sortable: false,
            width: '7%'
          },
          {
            text: '',
            sortable: false,
          },
        ],
        contents: [{
          no: '1',
          num:'7754-8808',
          code: 'IC290003',
          com: 'MOBILAND',
          num1: '예자인',
          num2: '010-1234-1234',
          num3: '32,000',
          num4: '32,000',
          num5: '32,000',
          num6: '2023-03-03  16:07:23',
          num7: '32,000'
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
  ::v-deep {
    .v-data-table__wrapper {
      tbody td:nth-child(3) {
        text-decoration: underline;
      }
    }
    @include mobile{
      .v-slide-group__content{
        justify-content: center;
      }
  }
  }
  .v-tabs{
      border-bottom:solid 2px #F0F2F5;
    }
    .v-tab{
      font-size: 1.6rem;
      font-weight: 400;
      letter-spacing:0;
      width:120px;
      color:#000 !important;
      &.v-tab--active{
        font-weight: 700;
        color:#2f79e8 !important;
        &:after{
          display: inline-block;
          content: '';
          width:100%;
          height: 4px;
          background: #2f79e8;
          position: absolute;bottom:0;
        }
      }
    }

  @include pc {
    .v-window{
      height: 100%;
    }
    .sch-table-wrap {
      .read{
            position: absolute;
    bottom: 20px;
    left: 24px;
      }
      .v-data-table {
        height: calc(100vh - 450px);
      }
    }
  }
    @include mobile{
      .read{
        padding: 10px;
        background: #fff;
      }
  }

</style>