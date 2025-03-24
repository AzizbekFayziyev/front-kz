<template>
  <Drawer :value="showContactsDrawer" @input="updateDrawer">
    <div class="drawer">
      <div class="drawer-nav">
        <p>Back</p>
        <div class="drawer-nav-back">
          <ArrowBackIcon
            class="drawer-nav-back-arrow"
            @click="$router.back()"
          />
          <span> All Contacts </span>
        </div>
      </div>
      <div class="drawer-card-wrapper">
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
        <div class="drawer-card">
          <div class="drawer-card-img">
            <img :src="require('@/assets/svg/user-image.png')" />
          </div>
          <div class="drawer-card-user">
            <div class="drawer-card-user-name">
              <span>Nickname</span>
              <span>@username</span>
            </div>
            <span class="drawer-card-user-id">ID: 999999</span>
          </div>
        </div>
      </div>
    </div>
  </Drawer>
</template>

<script>
import Drawer from '@/components/drawer.vue'
// @ts-ignore
import ArrowBackIcon from '@/assets/svg/arrow-back.svg?inline'

export default {
  name: 'ContactsDrawer',
  components: {
    Drawer,
    ArrowBackIcon,
  },
  props: {
    showContactsDrawer: Boolean,
  },
  methods: {
    updateDrawer(value) {
      this.$emit('update:showContactsDrawer', value)
    },
  },
}
</script>

<style lang="scss" scoped>
.drawer {
  display: flex;
  flex-direction: column;
  height: 80vh;
  margin: 12px;

  &-nav {
    p {
      font-family: 'Evolventa';
      color: #f64e2a;
      font-size: 14px;
      padding-bottom: 12px;
    }

    &-back {
      display: flex;
      gap: 10px;
      align-items: end;
      font-family: 'Hanson';
      font-weight: 700;
      line-height: 11px;
      text-transform: uppercase;
      margin-bottom: 30px;
    }
  }
  &-card-wrapper {
    flex: 1;
    overflow-y: auto;
  }
  &-card {
    display: flex;
    align-items: center;
    gap: 20px;
    border-top: 1px solid rgba(29, 28, 36, 0.5);
    border-bottom: 1px solid rgba(29, 28, 36, 0.5);
    padding: 8px 0;
    font-family: 'Reza Zulmi Alfaizi Sans';

    &-img img {
      width: 50px !important;
    }

    &-user {
      &-name {
        display: flex;
        gap: 4px;
        font-size: 14px;

        span:nth-child(2) {
          color: #ffffff80;
        }
      }
      &-id {
        font-size: 12px;
        color: #ffffff80;
      }
    }
  }
}

.contacts-card-drawer {
  margin: 10px 12px;
}

.contacts-card-drawer-wrapper {
  flex: 1;
  overflow-y: auto;
}

.contacts-card-drawer-wrapper::-webkit-scrollbar {
  width: 6px;
}
.contacts-card-drawer-wrapper::-webkit-scrollbar-thumb {
  border-radius: 10px;
}
.contacts-card-drawer-wrapper::-webkit-scrollbar-track {
  background: transparent;
}
</style>
