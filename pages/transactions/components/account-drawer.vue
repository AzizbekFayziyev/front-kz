<template>
  <Drawer v-model="showDrawer" :value="showDrawer" @input="updateDrawer">
    <div class="drawer">
      <span class="drawer-header">All Accounts</span>
      <div class="transactions-card-drawer-wrapper">
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-btc.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>0.015424 BTC</span>(≈ $1,456)
                <img :src="require('@/assets/svg/checked.svg')" />
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-ltc.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>1 LTC</span>(≈ $1,456)
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-eth.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>15 ETH</span>(≈ $1,456)
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-udt.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>15 UDT</span>(≈ $1,456)
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-btc.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>0.015424 BTC</span>(≈ $1,456)
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-ltc.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>1 LTC</span>(≈ $1,456)
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-eth.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>1 ETH</span>(≈ $1,456)
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
        <div
          class="transactions-card transactions-card-drawer"
          @click="showDrawer = true"
        >
          <div class="transactions-card-balance">
            <div class="transactions-card-balance-img">
              <img :src="require('@/assets/svg/transactions-udt.svg')" />
            </div>
            <div class="transactions-card-balance-amount">
              <div class="transactions-card-balance-amount-currency">
                <span>15 UDT</span>(≈ $1,456)
              </div>
              <span class="transactions-card-balance-amount-account"
                >BTC Account: ****235</span
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </Drawer>
</template>

<script>
import Drawer from '@/components/drawer.vue'

export default {
  name: 'AccountDrawer',
  components: {
    Drawer,
  },
  props: {
    showDrawer: Boolean,
  },
  methods: {
    updateDrawer(value) {
      this.$emit('update:showDrawer', value)
    },
  },
}
</script>

<style lang="scss" scoped>
.drawer {
  display: flex;
  flex-direction: column;
  height: 80dvh;

  &-header {
    text-align: center;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 16px;
    font-family: 'Hanson';
    margin: 16px 0 8px 0;
    position: sticky;
    top: 0;
    z-index: 10;
  }
}

.transactions-card {
  background-color: #1d1c24;

  &-drawer {
    margin: 10px 12px;
  }

  &-balance {
    &-img img {
      width: 75px;
      height: 68px;
    }
    &-amount {
      &-currency {
        display: flex;
        align-items: center;
        margin-bottom: 16px;

        img {
          margin-left: 8px;
        }
      }

      &-account {
        border-radius: 8px !important;
      }
    }
  }
}

.transactions-card-drawer-wrapper {
  flex: 1;
  overflow-y: auto;

  &::-webkit-scrollbar {
    width: 6px;
  }

  &::-webkit-scrollbar-thumb {
    border-radius: 10px;
  }

  &::-webkit-scrollbar-track {
    background: transparent;
  }
}
</style>
