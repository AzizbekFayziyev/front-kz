<template>
  <div>
    <div class="transactions">
      <div class="transactions-nav">
        <div class="transactions-nav-back">
          <ArrowBackIcon
            class="transactions-nav-back-arrow"
            @click="$router.back()"
          />
          Internal transfer
        </div>
      </div>
      <div>
        <swiper
          ref="swiper"
          :options="swiperOptions"
          @slideChange="onSlideChange"
        >
          <swiper-slide v-for="(card, index) in cards" :key="index">
            <div class="transactions-card" @click="showDrawer = true">
              <div class="transactions-card-balance">
                <div class="transactions-card-balance-img">
                  <img :src="card.icon" />
                </div>
                <div class="transactions-card-balance-amount">
                  <div class="transactions-card-balance-amount-currency">
                    <span>{{ card.amount }}</span
                    >(≈ {{ card.value }})
                  </div>
                  <span class="transactions-card-balance-amount-account">{{
                    card.account
                  }}</span>
                </div>
              </div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
      <div class="transactions-dots">
        <span
          v-for="(dot, index) in cards.length"
          :key="index"
          :class="['dot', { active: index === activeIndex }]"
          @click="goToSlide(index)"
        ></span>
      </div>
      <div v-if="!isInputLengthGreaterThanThree" class="transactions-contacts">
        <InputOracle
          user="true"
          placeholder="Username or ID"
          :v="inputValue"
          @changed="inputValue = $event"
        />
        <div class="transactions-contacts-wrapper">
          <div class="transactions-contacts-avatar">
            <div class="transactions-contacts-avatar-img">
              <img :src="require('@/assets/svg/user-image.png')" alt="" />
            </div>
            <span class="transactions-contacts-avatar-name">Nickname</span>
          </div>
          <div class="transactions-contacts-avatar">
            <div class="transactions-contacts-avatar-img">
              <img :src="require('@/assets/svg/user-image-2.svg')" alt="" />
            </div>
            <span class="transactions-contacts-avatar-name">Nickname</span>
          </div>
          <div class="transactions-contacts-avatar">
            <div class="transactions-contacts-avatar-img">
              <img :src="require('@/assets/svg/user-image-3.svg')" alt="" />
            </div>
            <span class="transactions-contacts-avatar-name">Nickname</span>
          </div>
          <div class="transactions-contacts-avatar">
            <div class="transactions-contacts-avatar-img">
              <img :src="require('@/assets/svg/user-image-4.svg')" alt="" />
            </div>
            <span class="transactions-contacts-avatar-name">Nickname</span>
          </div>
          <div class="transactions-contacts-avatar">
            <div class="transactions-contacts-avatar-img">
              <img :src="require('@/assets/svg/user-image-5.svg')" alt="" />
            </div>
            <span class="transactions-contacts-avatar-name">Nickname</span>
          </div>
          <div class="transactions-contacts-avatar">
            <div class="transactions-contacts-avatar-img">
              <img :src="require('@/assets/svg/user-image.png')" alt="" />
            </div>
            <span class="transactions-contacts-avatar-name">Nickname</span>
          </div>
          <div class="transactions-contacts-avatar">
            <div class="transactions-contacts-avatar-img">
              <img :src="require('@/assets/svg/user-image-2.svg')" alt="" />
            </div>
            <span class="transactions-contacts-avatar-name">Nickname</span>
          </div>
        </div>
        <div class="transactions-contacts-buttons">
          <div class="transactions-contacts-buttons-add">
            <div class="transactions-contacts-buttons-add-img">
              <img
                :src="require('@/assets/svg/add-currency-filled.svg')"
                alt=""
              />
            </div>
            <button class="transactions-contacts-buttons-add-btn">
              Add New Contact
            </button>
          </div>
          <div class="transactions-contacts-buttons-add">
            <button
              class="transactions-contacts-buttons-view-btn"
              @click="showContactsDrawer = true"
            >
              View All Contacts
              <img
                :src="require('@/assets/svg/tick.svg')"
                alt=""
                class="tick-icon"
              />
            </button>
          </div>
        </div>
      </div>
      <div v-if="isInputLengthGreaterThanThree" class="transactions-info-panel">
        <InputOracle
          placeholder="ID: 901941951"
          right-icon="CloseIcon"
          readonly="true"
          @clear="handleClearInput"
        />
        <div class="transactions-info-panel-wrapper">
          <div class="transactions-info-panel-card">
            <div class="transactions-info-panel-card-img">
              <img :src="require('@/assets/svg/profile.svg')" alt="" />
            </div>
            <span
              >Check <br />
              Profile</span
            >
          </div>
          <div class="transactions-info-panel-card">
            <div class="transactions-info-panel-card-img">
              <img :src="require('@/assets/svg/escrow.png')" alt="" />
            </div>
            <span
              >Check P2P<br />
              Reviews</span
            >
          </div>
          <div class="transactions-info-panel-card">
            <div class="transactions-info-panel-card-img">
              <img :src="require('@/assets/svg/escrow-reviews.svg')" alt="" />
            </div>
            <span
              >Check <br />
              Profile</span
            >
          </div>
          <div class="transactions-info-panel-card">
            <div class="transactions-info-panel-card-img">
              <img :src="require('@/assets/svg/shops.png')" alt="" />
            </div>
            <span
              >Check <br />
              Profile</span
            >
          </div>
          <div class="transactions-info-panel-card">
            <div class="transactions-info-panel-card-img">
              <img :src="require('@/assets/svg/profile.svg')" alt="" />
            </div>
            <span
              >Check <br />
              Profile</span
            >
          </div>
        </div>
      </div>
      <div class="transactions-exchange">
        <InputOracle placeholder="0.5 LTC" right-icon="LiteCoinIcon" />
        <div class="transactions-exchange-img">
          <img :src="require('@/assets/svg/transfer.svg')" alt="" />
        </div>
        <InputOracle placeholder="$52.12" right-icon="UsdIcon" />
        <div class="transactions-exchange-memo">
          <InputOracle placeholder="Memo" />
        </div>
      </div>
      <ButtonOracle
        text="Transfer"
        color="orange"
        @click="$router.push('transactions/confirm')"
      />
      <AccountDrawer :showDrawer.sync="showDrawer" />
      <ContactsDrawer :showContactsDrawer.sync="showContactsDrawer" />
    </div>
  </div>
</template>

<script lang="ts">
// @ts-ignore
import { Component, Vue } from 'nuxt-property-decorator'
// @ts-ignore
import { ref } from 'vue'
// @ts-ignore
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import AccountDrawer from './components/account-drawer.vue'
import ContactsDrawer from './components/contacts-drawer.vue'
// @ts-ignore
import ArrowBackIcon from '@/assets/svg/arrow-back.svg?inline'
// @ts-ignore
import BtcIcon from '@/assets/svg/btc.svg?inline'
import InputOracle from '~/components/input-oracle.vue'
// @ts-ignore
import 'swiper/css/swiper.css'

@Component({
  components: {
    ArrowBackIcon,
    BtcIcon,
    AccountDrawer,
    ContactsDrawer,
    InputOracle,
    Swiper,
    SwiperSlide,
  },
})
export default class TransactionPage extends Vue {
  showDrawer = ref(false)
  showContactsDrawer = ref(false)
  inputValue = ''
  activeIndex = 0

  cards = [
    {
      icon: require('@/assets/svg/transactions-btc.svg'),
      amount: '0.015424 BTC',
      value: '$1,456',
      account: 'BTC Account: ****235',
    },
    {
      icon: require('@/assets/svg/transactions-eth.svg'),
      amount: '0.5 ETH',
      value: '$1,200',
      account: 'ETH Account: ****123',
    },
    {
      icon: require('@/assets/svg/transactions-ltc.svg'),
      amount: '10 LTC',
      value: '$1,000',
      account: 'LTC Account: ****456',
    },
  ]

  swiperOptions = {
    loop: false,
    autoHeight: true,
    on: {
      slideChange: () => {
        this.activeIndex = this?.$refs.swiper.$swiper.activeIndex
      },
    },
  }

  $refs: any
  $router: any

  layout() {
    return 'mobile'
  }

  get isInputLengthGreaterThanThree(): boolean {
    return this.inputValue.length > 5
  }

  handleClearInput() {
    this.inputValue = ''
  }

  onSlideChange() {
    this.activeIndex = this?.$refs.swiper.$swiper.activeIndex
  }

  goToSlide(index: number) {
    this?.$refs.swiper.$swiper.slideTo(index)
  }
}
</script>

<style lang="scss">
.transactions {
  display: flex;
  flex-direction: column;
  margin-top: 18px;

  &-nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 10px;
    margin-bottom: 18px;

    &-back {
      display: flex;
      gap: 10px;
      align-items: end;
      font-family: 'Hanson';
      font-style: normal;
      font-weight: 700;
      font-size: 14px;
      line-height: 11px;
      text-transform: uppercase;

      &-arrow {
        cursor: pointer;
      }
    }
  }

  &-card {
    background-color: #121119;
    border-radius: 12px;
    padding: 12px;
    cursor: pointer;
    &-balance {
      display: flex;
      justify-items: center;
      align-items: center;
      gap: 16px;

      &-amount {
        font-size: 14px;
        color: #fff;
        &-currency {
          font-family: 'Evolventa';
          color: #ffffff99;
          margin-bottom: 16px;
          span {
            font-family: 'Hanson';
            margin-right: 6px;
            color: #fff;
          }
        }
        &-account {
          background-color: #191823;
          border-radius: 8px;
          padding: 6px 10px;
          line-height: 160%;
          font-family: 'Reza Zulmi Alfaizi Sans' !important;
          color: #fff;
        }
      }
    }
  }
  &-dots {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 6px;
    margin-top: 12px;
    margin-bottom: 20px;

    .dot {
      width: 8px;
      height: 8px;
      background-color: #211e2e;
      border-radius: 50%;
      transition: background-color 0.3s ease, width 0.3s ease, height 0.3s ease;
    }

    .dot.active {
      background-color: #f64e2a;
      width: 10px;
      height: 10px;
    }
  }
  &-contacts {
    background-color: #15151f;
    padding: 12px;
    border-radius: 12px;
    &-wrapper {
      display: flex;
      gap: 12px;
      overflow-x: auto;
      overflow-y: hidden;
      white-space: nowrap;
      scroll-behavior: smooth;
    }
    &-avatar {
      padding: 16px 0;
      img {
        width: 50px;
        height: 50px;
      }
      &-name {
        font-family: 'Kenyan Coffee';
      }
    }
    &-buttons {
      margin-top: 8px;
      display: flex;
      gap: 8px;
      font-size: 14px;

      button {
        font-family: 'Reza Zulmi Alfaizi Sans';
        border-radius: 6px;
        white-space: nowrap;
      }

      &-add {
        position: relative;
        width: 100%;
      }

      &-add-img {
        position: absolute;
        top: 7px;
        left: 4px;
      }

      &-add-btn,
      &-view-btn {
        border-radius: 6px;
        color: #fff;
        box-shadow: none;
        height: 32px;
      }
      &-add-btn {
        background-color: #15151f;
        padding-left: 20px;
      }
      &-view-btn {
        background-color: #262633;
        border: none;
        padding-right: 20px;
      }
    }
  }
  &-exchange {
    background-color: #15151f;
    padding: 8px;
    border-radius: 12px;
    margin-top: 20px;
    margin-bottom: 68px;
    &-img {
      display: flex;
      justify-content: center;
      padding: 6px 0;
      cursor: pointer;
    }
    &-memo {
      margin-top: 8px;
    }
  }
  &-info-panel {
    background-color: #121119;
    padding: 12px;
    border-radius: 12px;
    &-wrapper {
      display: flex;
      gap: 8px;
      overflow-x: auto;
      overflow-y: hidden;
      white-space: nowrap;
      scroll-behavior: smooth;
    }
    &-card {
      background-color: #1d1c24;
      border-radius: 8px;
      padding: 8px;
      margin-top: 12px;
      font-family: 'Kenyan Coffee';
      flex: 0 0 75px;

      &-img img {
        width: 42px;
      }
    }
  }
}
</style>
