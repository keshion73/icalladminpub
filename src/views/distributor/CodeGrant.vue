<template>
  <div>
    <PageTit>
      <div>
        <v-btn class="btntxt">가상계좌재발급</v-btn>
        <v-btn class="btnbg" @click="Modal = true">등록</v-btn>
      </div>
    </PageTit>
    <div class="page-bg" v-if="!$vuetify.breakpoint.xs">
      <div class="code-add">
        <div class="grid">
          <div class="grid-col" style="flex-direction: column;">
            <div class="d-flex">
              <div class="th">
                판매방식
              </div>
              <div class="td" style="padding:23px 20px">
                <v-radio-group class="code-radio" row v-model="radio01">
                  <v-radio label="대리점" value="대리점"></v-radio>
                  <v-radio label="총판" value="총판"></v-radio>
                </v-radio-group>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                대리점명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                대표자명
              </div>
              <div class="td">
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                주민번호
              </div>
              <div class="td d-flex">
                <v-text-field outlined></v-text-field>
                <span class="unit">-</span>
                <v-text-field outlined></v-text-field>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                사업자번호
              </div>
              <div class="td d-flex">
                <v-text-field outlined></v-text-field>
                <span class="unit">-</span>
                <v-text-field outlined style="width:135px"></v-text-field>
                <span class="unit">-</span>
                <v-text-field outlined></v-text-field>
              </div>
            </div>
          </div>
          <div class="grid-col">
            <div class="d-flex">
              <div class="th">
                사업자등록증
              </div>
              <div class="td">
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                신분증
              </div>
              <div class="td">
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                통장사본
              </div>
              <div class="td">
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                사전승낙서
              </div>
              <div class="td">
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                인감증명서
              </div>
              <div class="td">
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
              </div>
            </div>
          </div>
          <div class="grid-col">
            <div class="d-flex input-area">
              <div class="th">
                지역
              </div>
              <div class="td">
                <v-radio-group class="code-radio" row v-model="radio02">
                  <v-radio label="서울/경기" value="서울/경기"></v-radio>
                  <v-radio label="강원도" value="강원도"></v-radio>
                  <v-radio label="충청도" value="충청도"></v-radio>
                  <v-radio label="전라도" value="전라도"></v-radio>
                  <v-radio label="경상도" value="경상도"></v-radio>
                  <v-radio label="제주도" value="제주도"></v-radio>
                </v-radio-group>
              </div>
            </div>
            <div class="d-flex input-confile">
              <div class="th">
                계약서
              </div>
              <div class="td" style="padding:17px 20px">
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
                <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="code-add">
        <div class="grid">
          <div class="d-flex">
            <div class="th">
              이메일
            </div>
            <div class="td d-flex">
              <v-text-field outlined style="width:168px"></v-text-field>
              <span class="unit">@</span>
              <v-text-field outlined></v-text-field>
            </div>
          </div>
          <div class="d-flex">
            <div class="th">
              폰번호
            </div>
            <div class="td d-flex">
              <v-text-field outlined style="width:135px"></v-text-field>
              <span class="unit">-</span>
              <v-text-field outlined></v-text-field>
              <span class="unit">-</span>
              <v-text-field outlined></v-text-field>
            </div>
          </div>
          <div class="d-flex">
            <div class="th">
              일반전화
            </div>
            <div class="td d-flex">
              <v-text-field outlined style="width:135px"></v-text-field>
              <span class="unit">-</span>
              <v-text-field outlined></v-text-field>
              <span class="unit">-</span>
              <v-text-field outlined></v-text-field>
            </div>
          </div>
        </div>
        <div class="grid" style="grid-template-columns: 1fr 2fr;">
          <div class="d-flex">
            <div class="th">
              팩스
            </div>
            <div class="td d-flex">
              <v-text-field outlined style="width:135px"></v-text-field>
              <span class="unit">-</span>
              <v-text-field outlined></v-text-field>
              <span class="unit">-</span>
              <v-text-field outlined></v-text-field>
            </div>
          </div>
          <div class="d-flex">
            <div class="th">
              주소
            </div>
            <div class="td d-flex">
              <v-text-field outlined></v-text-field>
            </div>
          </div>
        </div>
      </div>
      <div class="code-add">
        <div class="grid" style="grid-template-columns: 2fr 1fr;">
          <div class="d-flex input-chk">
            <div class="th">
              상위대리점명
            </div>
            <div class="td d-flex">
              <v-text-field outlined></v-text-field>
              <v-checkbox label="상위 없음" color="#2F79E8"></v-checkbox>
            </div>
          </div>
          <div class="d-flex">
            <div class="th">
              영업 담당자
            </div>
            <div class="td d-flex">
              <v-select :items="items" outlined :menu-props="{ offsetY: true }" placeholder="선택">
              </v-select>
            </div>
          </div>
        </div>
        <div class="grid">
          <div class="d-flex">
            <div class="th">
              이체은행
            </div>
            <div class="td d-flex">
              <v-text-field outlined></v-text-field>
            </div>
          </div>
          <div class="d-flex">
            <div class="th">
              예금주명
            </div>
            <div class="td d-flex">
              <v-text-field outlined></v-text-field>
            </div>
          </div>
          <div class="d-flex">
            <div class="th">
              계좌번호
            </div>
            <div class="td d-flex">
              <v-text-field outlined></v-text-field>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="page-bg" v-if="$vuetify.breakpoint.xs">
      <div class="code-add">
        <div class="d-flex">
          <div class="th">
            판매방식
          </div>
          <div class="td" style="padding:23px 20px">
            <v-radio-group class="code-radio" row v-model="radio01">
              <v-radio label="대리점" value="대리점"></v-radio>
              <v-radio label="총판" value="총판"></v-radio>
            </v-radio-group>
          </div>
        </div>
        <div class="d-flex input-area">
          <div class="th">
            지역
          </div>
          <div class="td">
            <v-radio-group class="code-radio" row v-model="radio02">
              <v-radio label="서울/경기" value="서울/경기"></v-radio>
              <v-radio label="강원도" value="강원도"></v-radio>
              <v-radio label="충청도" value="충청도"></v-radio>
              <v-radio label="전라도" value="전라도"></v-radio>
              <v-radio label="경상도" value="경상도"></v-radio>
              <v-radio label="제주도" value="제주도"></v-radio>
            </v-radio-group>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            대리점명
          </div>
          <div class="td">
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            대표자명
          </div>
          <div class="td">
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            주민번호
          </div>
          <div class="td d-flex">
            <v-text-field outlined></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            사업자번호
          </div>
          <div class="td d-flex">
            <v-text-field outlined></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined style="width:135px"></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex input-confile">
          <div class="th">
            계약서
          </div>
          <div class="td" style="padding:17px 20px">
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
            <!-- 업로드시 추가파일 생성 -->
            <!-- <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input> -->
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            사업자등록증
          </div>
          <div class="td">
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            신분증
          </div>
          <div class="td">
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            통장사본
          </div>
          <div class="td">
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            사전승낙서
          </div>
          <div class="td">
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            인감증명서
          </div>
          <div class="td">
            <v-file-input outlined prepend-icon="파일" clear-icon="mdi-close" color="#fff"></v-file-input>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            이메일
          </div>
          <div class="td d-flex">
            <v-text-field outlined style="width:168px"></v-text-field>
            <span class="unit">@</span>
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            폰번호
          </div>
          <div class="td d-flex">
            <v-text-field outlined style="width:135px"></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            일반전화
          </div>
          <div class="td d-flex">
            <v-text-field outlined style="width:135px"></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            팩스
          </div>
          <div class="td d-flex">
            <v-text-field outlined style="width:135px"></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
            <span class="unit">-</span>
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            주소
          </div>
          <div class="td d-flex">
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex input-chk">
          <div class="th">
            상위대리점명
          </div>
          <div class="td d-flex">
            <v-text-field outlined></v-text-field>
            <v-checkbox label="상위 없음" color="#2F79E8"></v-checkbox>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            영업 담당자
          </div>
          <div class="td d-flex">
            <v-select :items="items" outlined :menu-props="{ offsetY: true }" placeholder="선택">
            </v-select>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            이체은행
          </div>
          <div class="td d-flex">
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            예금주명
          </div>
          <div class="td d-flex">
            <v-text-field outlined></v-text-field>
          </div>
        </div>
        <div class="d-flex">
          <div class="th">
            계좌번호
          </div>
          <div class="td d-flex">
            <v-text-field outlined></v-text-field>
          </div>
        </div>
      </div>
      <div class="code-btn">
        <v-btn class="btntxt" x-large>가상계좌재발급</v-btn>
        <v-btn class="btnbg" x-large @click="Modal = true">등록</v-btn>
      </div>
    </div>
    <!-- <Modal @close="Modal = false" v-if="Modal" :title="'대리점 코드부여'">
      <p slot="mes">대리점 코드를 부여하시겠습니까?<br>
        <span style="font-weight:500;color:#000;margin-top: 5px;display: block">대리점 명 : 1234<br>대리점 코드 : IC900098 </span> 
      </p>
      <div slot="btn">
        <v-btn class="btntxt" x-large>취소</v-btn>
        <v-btn class="btnbg" x-large>코드부여</v-btn>
      </div>
    </Modal> -->
    <Modal @close="Modal = false" v-if="Modal" :title="'하부 대리점 코드 부여'">
      <p slot="mes" style="width:100%">영문 대문자 3자를 입력해주세요.
        <v-text-field outlined></v-text-field>
      </p>
      <div slot="btn">
        <v-btn class="btntxt" x-large>취소</v-btn>
        <v-btn class="btnbg" x-large>코드부여</v-btn>
      </div>
    </Modal>
  </div>
</template>
<script>
import PageTit from "@/components/PageTit.vue";
  import Modal from "@/components/Modal.vue";
  export default {
    components: {
      PageTit,
      Modal
    },
    data() {
      return {
        radio01: '대리점',
        radio02: '서울/경기',
        items: ['영업 담당자1', '영업 담당자2', '영업 담당자3'],
        Modal:false,
      }
    },
  }
</script>

<style lang="scss" scoped>
  @import '~@/assets/scss/page/distributor/distributor.scss';

  .page-bg {
    padding: 40px 40px;

    .code-add {
      +.code-add {
        margin-top: 32px
      }

      .input-area {
        .v-radio {
          width: calc(33.33% - 6px);

          &:nth-child(3n + 1) {
            margin-left: 0 !important;
          }
        }
      }

      .input-confile {
        .v-input {
          +.v-input {
            margin-top: 12px
          }
        }
      }

      .input-chk {
        .v-text-field {
          max-width: 300px;
        }

        .v-input--checkbox {
          margin-left: 20px;
        }
      }
    }
  }

  ::v-deep {
    .v-input {
      position: relative;

      input {
        max-height: 48px !important;
      }

      .v-text-field__details {
        position: absolute;
        left: 0;
        bottom: -15px;
      }
    }

    .code-radio {
      padding-top: 0;
      margin-bottom: -8px;

      .v-radio {
        background: #fff;
        border: 1px solid #C7D1E3;
        width: 95px;
        height: 48px;
        line-height: 48px;
        justify-content: center;
        border-radius: 8px;
        cursor: pointer;
        color: #444;
        margin-bottom: 8px;

        +.v-radio {
          margin-left: 8px;
        }

        .v-input--selection-controls__input {
          display: none;
        }

        label {
          font-size: 1.4rem;
          display: inline-block;
          text-align: center;
          color: #000 !important
        }
      }

      .v-item--active {
        background: #2F79E8;
        border: solid 1px #2F79E8;

        label {
          color: #fff !important;
          font-weight: 700;
        }
      }
    }

    .v-file-input {
      &.primary--text {
        color: #fff !important;
        caret-color: #fff !important;
      }

      flex-direction: row-reverse;

      .v-input__slot {
        padding-right: 75px !important;
        overflow: hidden;
        min-height: 48px !important;

        .v-input__append-inner {
          margin-top: 15px;
          color: #ccc !important
        }
      }

      .v-input__append-inner {
        padding-right: 10px;

        .v-input__icon--clear {
          button {
            color: #000 !important;
            border: solid 1px #DBE1EB;
            border-radius: 100%;
            font-size: 14px;
            padding: 4px;
          }
        }
      }

      .v-input__prepend-outer {
        margin: 0;
        z-index: 2;

        .v-input__icon {
          background: #2F79E8;
          border: solid 1px #2F79E8;
          margin: 0;
          height: 48px;
          width: 72px;
          position: absolute;
          right: 0;
          border-radius: 0 8px 8px 0;

          button {
            color: #fff !important;
            font-size: 1.6rem;
            font-weight: 700;
          }
        }
      }

      &.error--text {
        .v-input__icon {
          border: solid 1px #E61E79 !important;
        }
      }
    }

    .input-chk {
      .v-input--checkbox {
        .v-input--selection-controls__input {
          margin-right: 0
        }

        .v-label {
          margin-left: 4px;
          font-size: 1.2rem;
          line-height: inherit !important;
        }
      }
    }

    .v-text-field input {
      &::placeholder {
        color: #000 !important
      }
    }
  }

  @include mobile {
    .input-chk {
      .d-flex {
        justify-content: space-between;
      }

      .v-text-field {
        max-width: 65% !important;
      }
    }
  }
</style>