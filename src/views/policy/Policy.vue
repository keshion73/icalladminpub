<template>
  <div>
    <PageTit>
      <div>
        <v-btn class="btnbg">저장</v-btn>
      </div>
    </PageTit>
    <div class="page-bg page-flex">
      <div class="sch-table-wrap">
        <div>
          <v-data-table :headers="headers" :items="contents" hide-default-footer mobile-breakpoint="0"
            :class="$vuetify.breakpoint.xs?'mobile-table':''">
            <template v-slot:item="{ item }">
              <tr>
                <td>{{item.com}}</td>
                <td>{{item.num1}}</td>
                <td>{{item.num2}}</td>
                <td>
                  <v-text-field outlined hide-details="auto"></v-text-field>
                </td>
                <td>
                  <v-text-field outlined hide-details="auto"></v-text-field>
                </td>
                <td>
                  <v-text-field outlined hide-details="auto"></v-text-field>
                </td>
                <td>
                  <v-text-field outlined hide-details="auto"></v-text-field>
                </td>
                <td></td>
              </tr>
            </template>
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
            width: '8%'
          },
          {
            text: '요금제명',
            value: 'num2',
            sortable: false,
            width: '15%'
          },
          {
            text: '개통',
            value: 'num3',
            sortable: false,
            width: '230px'
          },
          {
            text: '1달',
            value: 'num4',
            sortable: false,
            width: '230px'
          },
          {
            text: '2달',
            value: 'num5',
            sortable: false,
            width: '230px'
          },
          {
            text: '3달',
            value: 'num6',
            sortable: false,
            width: '230px'
          },
          {
            text: '',
            sortable: false,
          },
        ],
        contents: [{
          com: 'LGU',
          num1: '스마텔',
          num2: '선불 스마트 300M',
          num3: '개통',
          num4: '1달',
          num5: '2달',
          num6: '3달'
        }, ]
      }
    },
    computed: {},
  }
</script>

<style lang="scss" scoped>
  .sch-table-wrap {
    margin-top: 0;
  }

  ::v-deep {
      .v-data-table {
        tbody {
          tr:hover {
            background: none !important;
          }

          td {
            height: 64px !important;
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
</style>