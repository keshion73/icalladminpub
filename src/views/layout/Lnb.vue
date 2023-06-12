<template> 
<div>
  <v-navigation-drawer app permanent fixed :expand-on-hover="false" color="#161718" v-if="!$vuetify.breakpoint.mobile">
    <div class="mini-navi-top" v-if="mini">
      <div class="drawer-toggler cursor-pointer" :class="{ active: togglerActive }" @click="minifyDrawer">
        <img src="@/assets/images/common/icon-menux.svg" alt="">
      </div>
      <p class="logo"><img src="@/assets/images/icalllogo.svg" alt=""><span>관리자</span></p>
    </div>
    <div class="navi-top" v-if="!mini">
      <p class="logo"><img src="@/assets/images/icalllogo.svg" alt=""><span>관리자</span></p>
      <div class="drawer-toggler cursor-pointer" :class="{ active: togglerActive }" @click="minifyDrawer">
        <img src="@/assets/images/common/icon-menux.svg" alt="">
      </div>
    </div>
    <v-list v-if="!mini">
      <v-list-group v-for="(item, i) in submenu" :key="i" :ripple="false" active-class="item-active">
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>
              {{ item.title }}
            </v-list-item-title>
          </v-list-item-content>
        </template>

        <v-list-item v-for="(subItem, j) in item.item" :key="j" :to="subItem.to">
          <v-list-item-content>
            <v-list-item-title>
              {{ subItem.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-group>
    </v-list>
  </v-navigation-drawer>
  <div class="hd-wrap" v-if="$vuetify.breakpoint.xs">
      <div class="hd-cont">
        <div class="logo">
          <img src="@/assets/images/icalllogo.svg" alt=""><span>관리자</span>
        </div>
        <div :class="[{'active':drawer},'all-menu']" @click="drawer = true">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </div>
  <v-navigation-drawer v-if="$vuetify.breakpoint.xs" absolute width="250px" height="100vh" hide-overlay right v-model="drawer" temporary>
      <div class="mem-info"> 
      </div>
      <div class="sub-menu">
        <v-list>
         <v-list-group
        v-for="(item, i) in submenu"
        :key="i"
        :ripple="false"
      >
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title>
              {{ item.title }}
            </v-list-item-title>
          </v-list-item-content>
        </template>

        <v-list-item
          v-for="(subItem, j) in item.item"
          :key="j"
          :to="subItem.to"
        >
          <v-list-item-content>
            <v-list-item-title>
              {{ subItem.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-group>
      </v-list>
      </div>
    </v-navigation-drawer>
  
  </div>
</template>
<script>
  export default {
    name: "drawer",
    props: {
      drawer: {
        type: Boolean,
        default: null,
      },
    },
    data: () => ({
      mini: false,
      togglerActive: false,
      thirdLevelSimple: [
        "Third level menu",
        "Just another link",
        "One last link",
      ],
      submenu: [{
          title: 'Yesign(예자인)',
          item: [{
              title: '내정보',
              to: '/',
            },
            {
              title: '비밀번호 변경',
              to: '/'
            }
          ]
        }, {
          title: '개통',
          item: [{
              title: '개통 정보',
              to: '/opening/search',
            },
            {
              title: '개통 현황',
              to: '/opening/search'
            }
          ]
        },
        {
          title: '정책/요금',
          item: [{
              title: '정책관리',
              to: '/policy/policy',
            },
            {
              title: '요금제관리',
              to: '/policy/rateplan'
            },
            {
              title: '환불관리',
              to: '/policy/refund'
            }
          ]
        },
        {
          title: '정산',
          item: [{
              title: 'USIM 요청',
              to: '/',
            },
            {
              title: 'USIM 요청 내역',
              to: '/'
            }
          ]
        },
        {
          title: '총판/대리점',
          item: [{
              title: '대리점 관리',
              to: '/distributor/agency',
            },
            {
              title: '대리점 코드 등록',
              to: '/distributor/codegrant'
            },
            {
              title: '대리점 유심칩 관리',
              to: '/distributor/usim'
            }
          ]
        },
        {
          title: '관리자',
          item: [{
              title: 'USIM 요청',
              to: '/',
            },
            {
              title: 'USIM 요청 내역',
              to: '/'
            }
          ]
        },
        {
          title: '금액/예치금',
          item: [{
              title: '입출금 내역관리',
              to: '/amount/history',
            },
            {
              title: '예치금 관리',
              to: '/amount/deposit'
            },
            {
              title: '예치금 환불요청 조회',
              to: '/amount/refund'
            }
          ]
        },
        {
          title: '충전',
          item: [{
              title: '충전내역 조회',
              to: '/charge/chargehistory',
            },
            {
              title: '충전 통계',
              to: '/charge/chargestatistics'
            }
          ]
        },
      ],
    }),
    mounted() {},
    methods: {
      listClose(event) {
        let items;
        let headers;
        let groups;
        let currentEl;

        if (
          document.querySelectorAll(
            ".mb-0.v-list-item.v-list-item--link.item-active"
          )
        ) {
          items = document.querySelectorAll(
            ".mb-0.v-list-item.v-list-item--link.item-active"
          );
        }

        if (
          document.querySelectorAll(
            ".mb-0.v-list-item.v-list-item--link .v-list-group__header.v-list-item--active"
          )
        ) {
          headers = document.querySelectorAll(
            ".mb-0.v-list-item.v-list-item--link .v-list-group__header.v-list-item--active"
          );
        }

        if (
          document.querySelectorAll(
            ".mb-0.v-list-item.v-list-item--link .v-list-group .v-list .v-list-group.v-list-group--active, .mb-0.v-list-item.v-list-item--link .v-list-group.v-list-group--active"
          )
        ) {
          groups = document.querySelectorAll(
            ".mb-0.v-list-item.v-list-item--link .v-list-group .v-list .v-list-group.v-list-group--active, .mb-0.v-list-item.v-list-item--link .v-list-group.v-list-group--active"
          );
        }

        if (
          event.target.closest(
            ".mb-0.v-list-item.v-list-item--link .v-list-item__content.ms-6 .v-list-group"
          )
        ) {
          currentEl = event.target.closest(
            ".mb-0.v-list-item.v-list-item--link .v-list-item__content.ms-6 .v-list-group"
          );
        }

        if (items != null) {
          for (var i = 0; i < items.length; i++) {
            items[i].classList.remove("item-active");
          }
        }

        if (headers != null) {
          for (var j = 0; j < headers.length; j++) {
            headers[j].classList.remove(
              "v-list-item--active",
              "item-active",
              "primary--text"
            );
            headers[j].setAttribute("aria-expanded", false);
          }
        }

        if (groups != null) {
          for (var k = 0; k < groups.length; k++) {
            groups[k].classList.remove("v-list-group--active", "primary--text");
          }
        }

        if (event.target.closest(".mb-0.v-list-item.v-list-item--link")) {
          event.target
            .closest(".mb-0.v-list-item.v-list-item--link")
            .classList.add("item-active");
        }

        if (currentEl != null) {
          currentEl
            .querySelector(".v-list-group__header")
            .classList.add("v-list-item--active", "item-active");
        }
      },
      minifyDrawer() {
        this.togglerActive = !this.togglerActive;
        this.mini = !this.mini;
        const body = document.getElementsByTagName("body")[0];

      if (body.classList.contains("drawer-mini")) {
        body.classList.remove("drawer-mini");
      } else {
        body.classList.add("drawer-mini");
      }
        
      },
    },
  };
</script>