<template>
    <div>
        <div class="confirm">
            <div class="confirm-nav">
                <div class="confirm-nav-back">
                    <ArrowBackIcon class="confirm-nav-back-arrow" @click="$router.back()"/> Internal transfer
                </div>
            </div>
            <div class="confirm-wrapper">
                <div class="confirm-card">
                    <div class="confirm-card-img">
                        <img :src="require('@/assets/svg/btc-card-icon.svg')" alt="">
                    </div>
                </div>
                <div class="confirm-card">
                    <div class="confirm-card-img">
                        <img :src="require('@/assets/svg/recognize-scammers.svg')" alt="">
                    </div>
                </div>
                <div class="confirm-card">
                    <div class="confirm-card-img">
                        <img :src="require('@/assets/svg/transcan.svg')" alt="">
                    </div>
                </div>
            </div>
            <div class="confirm-transaction">
                <div class="confirm-transaction-account">
                    <div>
                        <span class="confirm-transaction-account-header">BTC Account</span>
                        <div class="confirm-transaction-account-balance">
                            <div class="confirm-transaction-account-balance-icon-wrapper">
                                <BtcIcon class="confirm-transaction-account-balance-icon"/>
                                <span class="confirm-transaction-account-balance-quantity">0.1</span>
                            </div>
                            <span class="confirm-transaction-account-balance-amount">≈ $10,901.25</span>
                        </div>
                        <div class="confirm-transaction-account-user">
                            <div class="confirm-transaction-account-user-img">
                                <img :src="require('@/assets/svg/user-image.png')" alt="">
                            </div>
                            <div class="confirm-transaction-account-user-wrapper">
                                <span class="confirm-transaction-account-user-name">Nickname</span>
                                <span>Internal Transfer by Username</span>
                                <span class="confirm-transaction-account-user-id">ID: 910491491</span>
                                <span class="confirm-transaction-account-user-fees">Fees: <strong>0.01%</strong></span>
                                <span class="confirm-transaction-account-user-commission">Commission 1,06 $</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="confirm-transaction-wrapper">
                    <div class="confirm-transaction-card">
                        <div class="confirm-transaction-card-img">
                            <img :src="require('@/assets/svg/profile.svg')" alt="">
                        </div>
                        <span>Check <br> Profile</span>
                    </div>
                    <div class="confirm-transaction-card">
                        <div class="confirm-transaction-card-img">
                            <img :src="require('@/assets/svg/escrow.png')" alt="">
                        </div>
                        <span>Check <br> Profile</span>
                    </div>
                    <div class="confirm-transaction-card">
                        <div class="confirm-transaction-card-img">
                            <img :src="require('@/assets/svg/escrow-reviews.svg')" alt="">
                        </div>
                        <span>Check <br> Profile</span>
                    </div>
                    <div class="confirm-transaction-card">
                        <div class="confirm-transaction-card-img">
                            <img :src="require('@/assets/svg/shops.png')" alt="">
                        </div>
                        <span>Check <br> Profile</span>
                    </div>
                    <div class="confirm-transaction-card">
                        <div class="confirm-transaction-card-img">
                            <img :src="require('@/assets/svg/profile.svg')" alt="">
                        </div>
                        <span>Check <br> Profile</span>
                    </div>
                </div>
            </div>
        </div>
        <ButtonOracle text="Confirm transfer" color="orange" @click="$router.push('receipt')"/>
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
    }
})
export default class ConfirmPage extends Vue {
    layout() {
        return 'mobile'
    }
}
</script>

<style lang="scss">

.confirm {
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
            font-family: "Hanson";
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
        border: 1px solid #F64E2A;
        cursor: pointer;
        flex: 0 0 133px;

        &::after {
            content: "";
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
        background-color:#121119;
        padding: 12px;
        border-radius: 12px;
        margin-top: 20px;
        &-wrapper {
            display: flex;
            gap: 8px;
            overflow-x: auto;
            overflow-y: hidden;
            white-space: nowrap;
            scroll-behavior: smooth;
        }
        &-card {
            background-color: #1D1C24;
            border-radius: 8px;
            padding: 8px;
            margin-top: 12px;
            font-family: 'Kenyan Coffee';
            flex: 0 0 75px;

            &-img img {
                width: 42px;
            }
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
                    color: #FFFFFF33;
                    font-family: 'Hanson';
                    font-weight: 700;
                    margin-bottom: 24px;
                }
            }
            &-user {
                display: block;
                flex-direction: column;
                &-name{
                    font-family: 'Kenyan Coffee';
                    font-size: 20px;
                    margin-bottom: 4px;
                }
                &-id {
                    color: #FFFFFF4D;
                    margin-top: 4px;
                }
                &-fees {
                    color: #FFFFFF4D;
                    margin-top: 20px;
                    strong {
                        color: #fff;
                        text-decoration: underline;
                    }
                }
                &-commission {
                    font-size: 10px;
                    color: #FFFFFF4D;
                    margin-top: 8px;
                }
            }
            &-user-wrapper {
                display: flex;
                flex-direction: column;
           }
        }
    }  

}
</style>
