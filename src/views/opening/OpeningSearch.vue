<template>
  <div>
    <PageTit>
      <div>
        <v-btn class="btnbg"><img src="@/assets/images/common/icon-add.svg" />등록</v-btn>
      </div>
    </PageTit>
    <div class="page-bg">
      <div class="sch-wrap d-flex">
        <div class="d-flex">
          <div>
            <div class="d-flex sch-input">
              <div class="th">
                조회구분
              </div>
              <div class="td">
                <v-select v-model="selected" :items="items" outlined :menu-props="{ offsetY: true }"></v-select>
              </div>
            </div>
            <!-- 개통일자일때 -->
            <div class="d-flex sch-input input-date" v-if="selected == '개통일자'">
              <div class="th">
                일자
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
                </div>
              </div>
            </div>
            <!-- 전화번호일때 -->
            <div class="d-flex sch-input" v-if="selected == '전화번호'">
              <div class="th">
                전화번호
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
          </v-data-table>
          <p class="read font-weight-bold">조회 <span style="color:#2F79E8">32</span></p>
          <v-pagination v-model="page" :length="15" :total-visible="7" circle active-color="#2F79E8"></v-pagination>
        </div>
      </div>
      <div class="detail-wrap">
        <div class="page-tit">
          <h2 class="text-h2 font-weight-bolder">상세보기</h2>
          <v-btn class="btnbg">등록</v-btn>
        </div>
        <div class="sch-wrap d-flex">
        <div class="d-flex">
          <div>
            <div class="d-flex sch-input">
              <div class="th">
                고객번호
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                명의
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                선택
              </div>
              <div class="td">
                <v-select v-model="selected" :items="items" outlined :menu-props="{ offsetY: true }"></v-select>
              </div>
            </div>            
          </div>
        </div>
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
        selected: '개통일자',
        items: ['개통일자', '전화번호'],
        page: 1,
        headers: [{
            text: '순번',
            value: 'no',
            sortable: false,
            width: '4%'
          },
          {
            text: '대리점',
            value: 'num',
            sortable: false,
          },
          {
            text: '휴대폰 번호',
            value: 'tel',
            sortable: false,
            width: '8%'
          },
          {
            text: '명의',
            value: 'num1',
            sortable: false,
            width: '4%'
          },
          {
            text: '통신사',
            value: 'num2',
            sortable: false,
            width: '4%'
          },
          {
            text: '유심번호',
            value: 'num3',
            sortable: false,
            width: '7%'
          },
          {
            text: '충전여부',
            value: 'num4',
            sortable: false,
          },
          {
            text: '요금제명',
            value: 'num5',
            sortable: false,
            width: '8%'
          },
          {
            text: '회선상태',
            value: 'num6',
            sortable: false,
          },
          {
            text: '고객식별번호',
            value: 'num7',
            width: '8%'
          },
          {
            text: '개통일',
            value: 'num8',
            sortable: false,
          },
          {
            text: '해지일',
            value: 'num9',
            sortable: false,
          },
          {
            text: '충전횟수',
            value: 'num10',
            sortable: false,
          },
          {
            text: '첫충전',
            value: 'num11',
            sortable: false,
          },
          {
            text: '스팸 회선여부',
            value: 'num12',
            sortable: false,
          },
          {
            text: '스팸회선적용',
            value: 'num13',
            sortable: false,
          },
        ],
        contents: [{
          no: '1',
          num: 'MOBILAND',
          tel: '010-1234-1234',
          num1: '*훈*',
          num2: 'SKT',
          num3: 'S05138013513',
          num4: '충전',
          num5: 'SKT 300mb',
          num6: '정상',
          num7: 'OEF05100031',
          num8: '23-05-13',
          num9: '23-08-12',
          num10: '1회',
          num11: '23-05-13',
          num12: '스팸',
          num13: '23-05-13',
        }, ]
      }
    },
    computed: {},
  }
</script>

<style lang="scss" scoped>
  .input-date .v-input {
    max-width: initial;
  }

  ::v-deep {
    @include pc {
      .v-data-table {
        thead {
          th {
            padding: 0 2px !important;

            &:first-child {
              padding-left: 20px !important;
            }
          }
        }

        tbody {
          tr:hover {
            background: none !important;
          }

          td {
            padding: 0 2px !important;

            &:first-child {
              padding-left: 20px !important;
            }
          }

          .v-input {
            background: #F8FAFC;

            input {
              height: 48px;
            }
          }
        }
      }
    }
  }
  @include pc {
    
    .page-bg{
      background: none !important;
      .detail-wrap{
        box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.07);
      }
    }
    .sch-table-wrap {
      box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.07);
      .read{
            position: absolute;
    bottom: 20px;
    left: 24px;
      }
      .v-data-table {
        height: 600px;
      }
    }
  }
</style>