<template>
  <v-overlay z-index="10000">
    <div class="modal-layer">
      <div style="height:calc(100% - 80px);">
        <div class="modal-tit">
          <h4 class="text-h4">MOBILAND</h4>
          <v-btn @click="$emit('close')"><img src="@/assets/images/common/icon-x.svg" alt=""></v-btn>
        </div>
        <div class="modal-cont">
          <div class="input-add">
            <div class="d-flex">
              <div class="th">
                지역
              </div>
              <div class="td">
                <v-select :items="['서울/경기']" outlined :menu-props="{ offsetY: true }" placeholder="지역">
                </v-select>
              </div>
            </div>
            <div class="d-flex">
              <div class="th">
                판매방식
              </div>
              <div class="td">
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
            <div class="d-flex input-confile">
              <div class="th">
                계약서
              </div>
              <div class="td">
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
                <v-autocomplete outlined append-icon="" :items="['12', '43', '25']"></v-autocomplete>
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
        </div>
      </div>
      <div class="modal-btn">
        <v-btn class="btnbg" block x-large>저장</v-btn>
      </div>
    </div>
  </v-overlay>
</template>

<script>
  export default {
  }
</script>

<style lang="scss" scoped>
  .modal-layer {
    background: #FFFFFF;
    box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.2);
    border-radius: 12px;
    width: 360px;
    height: 700px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-direction: column;
    color: #666666;

    >div {
      width: 100%;
    }

    .modal-tit {
      display: flex;
      width: 100%;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 24px;
      padding: 20px 30px 0;

      h4 {
        font-size: 1.6rem !important;
        color: #000 !important
      }

      .v-btn {
        padding: 0;
        min-width: auto;
        height: auto;
        background: none;
      }
    }

    .modal-cont {
      height: calc(100% - 74px);
      overflow: auto;
      padding: 0 20px 0 30px;

      .input-add {
        >.d-flex {
          flex-direction: column;

          +.d-flex {
            margin-top: 20px;
          }
        }
      }

      .input-add {
        .th {
          font-weight: 500;
          color: #000;
          margin-bottom: 8px;
        }

        .td {
          &.d-flex {
            align-items: center;
          }

          span.unit {
            margin: 0 7px 8px;
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
            margin-left: 4px;
          }
        }
      }

    }

    .modal-btn {
      padding: 0 30px 20px;
    }
  }

  ::v-deep {

    .v-input {
      position: relative;

      fieldset {
        border: 1px solid #C7D1E3
      }

      input {
        max-height: 48px !important;
        color: rgba(0, 0, 0, 0.87);
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

        .fa-square {
          font-size: 1.7rem;

          &::before {
            color: #C7D1E3;
          }
        }

        .fa-check-square {
          font-size: 1.7rem;
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
</style>