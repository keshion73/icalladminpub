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
                요청번호
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                변경구분
              </div>
              <div class="td">
                <v-select v-model="selected" :items="items" outlined :menu-props="{ offsetY: true }"></v-select>
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
                <td>{{item.num}}</td>
                <td>{{item.code}}</td>
                <td>{{item.com}}</td>
                <td>{{item.num1}}</td>
                <td>{{item.num2}}</td>
                <td>{{item.num3}}</td>
                <td :class="{pro01:item.num4 == '진행',pro02:item.num4 == '보류'}" class="td-pro"><span v-if="item.num4 !== '완료'"></span>{{item.num4}}</td>
                <td>{{item.num5}}</td>
                <td>{{item.num6}}</td>
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
         selected: '전체',
        items: ['전체','선택1', '선택2', '선택3'],
        page: 1,
        headers: [
          {
            text: '환불요청번호',
            value: 'num',
            sortable: false,
            width: '13%'
          },
          {
            text: '대리점코드',
            value: 'code',
            sortable: false,
            width: '7%'
          },
          {
            text: '대리점명',
            value: 'com',
            sortable: false,
            width: '8%'
          },
          {
            text: '요청금액',
            value: 'num1',
            sortable: false,
            width: '7%'
          },
          {
            text: '사유',
            value: 'num2',
            sortable: false,
            width: '13%'
          },
          {
            text: '결과 사유',
            value: 'num3',
            sortable: false,
            width: '13%'
          },
          {
            text: '진행상황',
            value: 'num4',
            sortable: false,
            width: '7%'
          },
          {
            text: '변경일',
            value: 'num5',
            sortable: false,
            width: '10%'
          },
          {
            text: '담당자',
            value: 'num6',
            sortable: false,
            width: '7%'
          },          
          {
            text: '',
            sortable: false,
          },
        ],
        contents: [{
          num:'RIC29000302304280002',
          code: 'IC290003',
          com: 'MOBILAND',
          num1: '32,000',
          num2: '-',
          num3: '-',
          num4: '진행',
          num5: '2023-03-03  16:07:23',
          num6: '예자인',
        },
        {
          num:'RIC29000302304280002',
          code: 'IC290003',
          com: 'MOBILAND',
          num1: '32,000',
          num2: '-',
          num3: '-',
          num4: '보류',
          num5: '2023-03-03  16:07:23',
          num6: '예자인',
          },
        {
          num:'RIC29000302304280002',
          code: 'IC290003',
          com: 'MOBILAND',
          num1: '32,000',
          num2: '-',
          num3: '-',
          num4: '완료',
          num5: '2023-03-03  16:07:23',
          num6: '예자인',
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
  table .td-pro{
    &.pro01{
      color:#12A389;
      span{
        background: #12A389;
      }
    }
    &.pro02{
      color:#DD214E;
      span{
        background: #DD214E;
      }
    }
    span{
      width:12px;
      height: 12px;
      border-radius: 100%;
      margin-right:8px;
      display: inline-block;
          vertical-align: middle;
    }
  }
}
  ::v-deep {
    .v-data-table__wrapper {
      tbody td:nth-child(3) {
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
        height: calc(100vh - 400px);
      }
    }
  }

</style>