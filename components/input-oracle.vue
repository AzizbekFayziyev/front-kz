<template>
  <div :class="inputClass">
    <label v-if="label" class="label">{{ label }}</label>
    <SearchIcon v-if="search" class="input-search" />
    <UserCircleIcon v-if="user" class="input-search" />
    <input v-model="value" :type="type" :placeholder="placeholder" :style="{ paddingLeft }" :readonly="readonly" />
    <component v-if="rightIcon" :is="rightIcon" class="input-right-action" @click="handleRightIconClick"/>
  </div>
</template>
<script lang="ts">
import { Component, Prop, Vue, Watch } from 'nuxt-property-decorator'
// @ts-ignore
import TrashIcon from '@/assets/svg/trash.svg?inline'
// @ts-ignore
import SearchIcon from '@/assets/svg/search.svg?inline'
// @ts-ignore
import UserCircleIcon from '@/assets/svg/user-circle.svg?inline'
// @ts-ignore
import LiteCoinIcon from '@/assets/svg/litecoin-ltc.svg?inline'
// @ts-ignore
import UsdIcon from '@/assets/svg/usd.svg?inline'
// @ts-ignore
import CloseIcon from '@/assets/svg/close-circle.svg?inline'

@Component({
  components: {
    TrashIcon,
    SearchIcon,
    UserCircleIcon,
    LiteCoinIcon,
    UsdIcon,
    CloseIcon
  }
})
export default class InputOracle extends Vue {
  @Prop({ default: '' }) readonly placeholder!: string
  @Prop({ default: '' }) readonly label!: string
  @Prop({ default: '' }) readonly type!: string
  @Prop({ default: '' }) readonly size!: string
  @Prop({ default: '' }) readonly v!: string
  @Prop({ default: false }) readonly search!: boolean
  @Prop({ default: false }) readonly user!: boolean
  @Prop({ default: false }) readonly readonly!: boolean
  @Prop({ default: null }) readonly rightIcon!: any
  @Prop({ default: null }) readonly trashAction?: Function

  value = ''

  @Watch('value')
  onChildChanged() {
    this.$emit('changed', this.value)
  }
  
  handleRightIconClick() {
    if (this.rightIcon === 'CloseIcon') {
      this.value = '';
      this.$emit('clear');
    }
  }


  get computedValue() {
    return this.value
  }

  get inputClass() {
    return ['input', this.size]
  }

  get paddingLeft() {
    return this.search || this.user ? '30px' : '10px';
  }

  created() {
    this.value = this.v;
  }
}
</script>
<style lang="scss">
.label {
  margin-bottom: 10px;
  font-family: 'Reza Zulmi Alfaizi Sans';
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
}

.input {
  display: flex;
  justify-content: center;
  flex-direction: column;
  font-size: 16px;
  position: relative;


  &-search {
    position: absolute;
    left: 5px;
  }

  &-user {
    position: absolute;
    left: 5px;
  }

  &.big {
    input {
      font-size: 24px;
    }
  }

  &-right-action {
    position: absolute;
    cursor: pointer;
    bottom: 9px;
    right: 11px;
  }

  input {
    box-sizing: border-box;
    padding: 10px 12px;
    width: 100%;
    height: 41px;
    background: #1e1d26;
    border-radius: 8px;
    font-family: 'Reza Zulmi Alfaizi Sans';
    font-weight: 400;
    color: #ffffff;
    border: none;
    outline: none;

    &::placeholder {
      font-family: 'Reza Zulmi Alfaizi Sans';
      font-weight: 400;
      color: rgba(255, 255, 255, 0.4);
    }
  }
}
</style>
