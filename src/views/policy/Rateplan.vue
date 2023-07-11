<template>
  <div>
    <PageTit>
      <div>
        <v-btn class="btntxt"><img src="@/assets/images/common/icon-excel.svg" />엑셀 다운로드</v-btn>
        <v-btn class="btnbg"><img src="@/assets/images/common/icon-add.svg" />요금제 추가</v-btn>
      </div>
    </PageTit>
    <div class="page-bg page-flex">
      <div class="sch-table-wrap">
        <div>
          <v-data-table :headers="headers" :items="contents" hide-default-footer mobile-breakpoint="0"
            :class="$vuetify.breakpoint.xs?'mobile-table':''">
          </v-data-table>
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
            text: '통신사',
            value: 'com',
            sortable: false,
            width: '8%'
          },
          {
            text: 'MVNO',
            value: 'num1',
            sortable: false,
            width: '10%'
          },
          {
            text: '요금제명',
            value: 'num2',
            sortable: false,
            width: '15%'
          },
          {
            text: '요금제 코드',
            value: 'num3',
            sortable: false,
            width: '10%'
          },
          {
            text: '외부연동 요금제 코드',
            value: 'num4',
            sortable: false,
          },
          {
            text: '기타',
            value: 'num5',
            sortable: false,
          },
          {
            text: '등록자 ID',
            value: 'num6',
            sortable: false,
            width: '10%'
          },
          {
            text: '사용 여부',
            value: 'num7',
            sortable: false,
          },
        ],
        contents: [{
          com: 'LGU',
          num1: '스마텔',
          num2: '선불 스마트 300M',
          num3: '-',
          num4: '1달',
          num5: '2달',
          num6: 'admin',
          num7: '사용'
        }, ]
      }
    },
    computed: {},
  }
</script>

<style lang="scss" scoped>
.page-bg{background:#fff}
  .sch-table-wrap {
    margin-top: 0;
  }

  ::v-deep {
    @include pc {
      .v-data-table__wrapper{
    height: calc(100vh - 160px);
  }
      .v-data-table {
        tbody {
          tr:hover {
            background: none !important;
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
    @include mobile{
        .sch-table-wrap .mobile-table {
        min-height: 73vh;
      }
    }
  }
</style>