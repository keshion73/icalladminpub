<template>
  <div>
    <PageTit />
    <div class="page-bg page-flex">
      <div class="sch-wrap d-flex">
        <div class="d-flex">
          <div>
            <div class="d-flex sch-input">
              <div class="th">
                코드명
              </div>
              <div class="td">
                <v-text-field outlined>
                </v-text-field>
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
            <div class="d-flex sch-input">
              <div class="th">
                주소
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
          </div>
          <div>
            <div class="d-flex sch-input">
              <div class="th">
                지역
              </div>
              <div class="td">
                <v-select v-model="selected" :items="items" outlined :menu-props="{ offsetY: true }"></v-select>
              </div>
            </div>
            <div class="d-flex sch-input">
              <div class="th">
                담당자
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
        <v-data-table :headers="headers" :items="contents" :items-per-page="100" hide-default-footer :mobile-breakpoint="0"
        :class="$vuetify.breakpoint.xs?'mobile-table':''">
        </v-data-table>
        <v-pagination v-model="page" :length="15" :total-visible="7" circle active-color="#2F79E8"></v-pagination>
      </div>
    </div>
    </div>
    <!-- <ModalInput></ModalInput> -->
  </div>
</template>
<script>
  import ModalInput from '../../components/ModalInput'
import PageTit from "@/components/PageTit.vue";
  export default {
    components: {
    ModalInput,
      PageTit
    },
    data() {
      return {
        selected: '전체',
        items: ['전체','선택1', '선택2', '선택3'],
        page: 1,
        headers: [{
            text: '코드명',
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
            text: '영업 시작일',
            value: 'date',
            sortable: false,
            width: '10%'
          },
          {
            text: '영업 상태',
            value: 'open',
            sortable: false  
          },
          {
            text: '담당자 명',
            value: 'name',
            sortable: false  
          },
          {
            text: '판매 구분',
            value: 'age',
            sortable: false  
          },
          {
            text: '전화번호',
            value: 'tel',
            sortable: false,
            width: '10%'
          },
          {
            text: '일반번호',
            value: 'tel2',
            sortable: false,
            width: '10%'
          },
          {
            text: '지역',
            value: 'area',
            sortable: false  
          },
          {
            text: '주소',
            value: 'add',
            sortable: false,
             width: '18%'
          },
          {
            text: '영업',
            value: 'open2',
            sortable: false,
            width: '10%'
          },
        ],
        contents: [{
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
          add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
          },
          {
            code: 'IC290003',
            com: 'MOBILAND',
            date: '2023-03-03  16:07:23',
            open: '영업',
            name: '예자인',
            age: '대리점',
          tel: '010-7754-8808',
          tel2: '010-7754-8808',
          area: '서울/경기',
            add: '경기 안산시 단원구 다움화1길 41-1',
            open2: '영업',
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
  @import '~@/assets/scss/page/distributor/distributor.scss';
  ::v-deep{
  .v-data-table__wrapper{
    width:auto;
    min-width: 1280px;
    height: calc(100vh - 400px);
    tbody .text-start:first-child{
      text-decoration: underline;
    }
    
  table{
    thead{
      position: sticky;
      top:0;
    }
  }
  }
}
@include pc {
.sch-table-wrap .v-data-table{
  max-width: 100%;
    overflow: auto;
}
}
@include mobile {
  .sch-table-wrap{
    .mobile-table {
    min-height: 300px;
    }
  }
}
</style>