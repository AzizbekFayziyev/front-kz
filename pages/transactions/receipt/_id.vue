<template>
  <div>
    <div class="receipt">
      <div class="receipt-nav">
        <div class="receipt-nav-back">
          <ArrowBackIcon
            class="receipt-nav-back-arrow"
            @click="$router.back()"
          />
          Internal transfer
        </div>
      </div>
      <div class="receipt-transaction">
        <div class="receipt-transaction-account">
          <div>
            <span class="receipt-transaction-account-header">BTC Account</span>
            <div class="receipt-transaction-account-balance">
              <div class="receipt-transaction-account-balance-icon-wrapper">
                <BtcIcon class="receipt-transaction-account-balance-icon" />
                <span class="receipt-transaction-account-balance-quantity"
                  >0.1</span
                >
              </div>
              <span class="receipt-transaction-account-balance-amount"
                >≈ $10,901.25</span
              >
            </div>
            <div class="receipt-transaction-account-user">
              <div class="receipt-transaction-account-user-img">
                <img :src="require('@/assets/svg/user-image.png')" alt="" />
              </div>
              <div class="receipt-transaction-account-user-wrapper">
                <span class="receipt-transaction-account-user-name"
                  >Nickname</span
                >
                <span>Internal Transfer by Username</span>
                <span class="receipt-transaction-account-user-id"
                  >ID: 910491491</span
                >
                <span class="receipt-transaction-account-user-fees"
                  >Fees: <strong>0.01%</strong></span
                >
              </div>
            </div>
          </div>
        </div>
        <div class="receipt-transaction-buttons-wrapper">
          <div class="receipt-transaction-buttons">
            <div class="receipt-transaction-buttons-child">
              <div class="receipt-transaction-buttons-img">
                <img :src="require('@/assets/svg/archive-check.svg')" alt="" />
              </div>
              <span>Add User</span>
            </div>
          </div>
          <div class="receipt-transaction-buttons">
            <div class="receipt-transaction-buttons-child">
              <div class="receipt-transaction-buttons-img">
                <img
                  :src="require('@/assets/svg/clipboard-check.svg')"
                  alt=""
                />
              </div>
              <span>Check History</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <ButtonOracle text="That's it" color="orange" @click="$router.push('')" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
// @ts-ignore
import ArrowBackIcon from '@/assets/svg/arrow-back.svg?inline'
// @ts-ignore
import BtcIcon from '@/assets/svg/btc.svg?inline'

@Component({
  components: {
    ArrowBackIcon,
    BtcIcon,
  },
})
export default class ReceiptPage extends Vue {
  layout() {
    return 'mobile'
  }
}
</script>

<style lang="scss">
.receipt {
  display: flex;
  flex-direction: column;
  margin-top: 18px;
  margin-bottom: 16px;

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

  &-wrapper {
    display: flex;
    gap: 8px;
    overflow-x: auto;
    overflow-y: hidden;
    white-space: nowrap;
    scroll-behavior: smooth;
  }

  &-card {
    position: relative;
    width: 133px;
    height: 158px;
    border-radius: 12px;
    border: 1px solid #f64e2a;
    cursor: pointer;
    flex: 0 0 133px;

    &::after {
      content: '';
      position: absolute;
      inset: 0;
      border: 4px solid black;
      border-radius: 12px;
      z-index: 1;
      pointer-events: none;
    }

    &-img {
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        border-radius: 16px;
      }
    }
  }
  &-transaction {
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
    }
    &-account {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      font-family: 'Reza Zulmi Alfaizi Sans';
      &-header {
        font-size: 14px;
      }
      &-balance {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
        margin-top: 12px;
        &-icon-wrapper {
          display: flex;
          justify-items: center;
          align-items: center;
          gap: 8px;
        }
        &-icon-wrapper span {
          margin-top: 8px;
          font-family: 'Hanson';
          font-weight: 700;
          font-size: 24px;
          line-height: 140%;
        }
        &-icon {
          background: #fff;
          padding: 6px 9px;
          border-radius: 50%;
        }
        &-amount {
          color: #ffffff33;
          font-family: 'Hanson';
          font-weight: 700;
          margin-bottom: 24px;
        }
      }
      &-user {
        display: block;
        flex-direction: column;
        &-name {
          font-family: 'Kenyan Coffee';
          font-size: 20px;
          margin-bottom: 4px;
        }
        &-id {
          color: #ffffff4d;
          margin-top: 4px;
        }
        &-fees {
          color: #ffffff4d;
          margin-top: 20px;
          strong {
            color: #fff;
            text-decoration: underline;
          }
        }
        &-commission {
          font-size: 10px;
          color: #ffffff4d;
          margin-top: 8px;
        }
      }
      &-user-wrapper {
        display: flex;
        flex-direction: column;
      }
    }

    &-buttons {
      width: 160px !important;
      margin-top: 12px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      box-sizing: border-box;
      width: 100%;
      background: #121119;
      border-radius: 12px;
      padding: 1px;
      background-image: linear-gradient(
        to right bottom,
        #eb4b2a,
        #232130,
        #232130
      );
      background-color: #121119;
      background-clip: padding-box, border-box;

      &-child {
        cursor: pointer;
        background-color: #121119;
        border-radius: 12px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        width: 100%;
        height: 100%;
        padding: 16px;
        box-sizing: border-box;
        background-image: linear-gradient(
          to right bottom,
          rgba(235, 75, 42, 0.2),
          rgba(35, 33, 48, 0.2),
          rgba(35, 33, 48, 0.2)
        );
      }

      &-wrapper {
        font-family: 'Reza Zulmi Alfaizi Sans';
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 12px;
      }
      &-img img {
        width: 30px;
        height: 30px;
        margin-bottom: 12px;
      }
    }
  }
}
</style>
