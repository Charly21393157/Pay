<template>
  <div class="examples">
    <div>
      <div class="example">
        <div class="title">Static Example</div>
        <div class="demo">
          <google-pay-button
            environment="PRODUCTION"
            button-type="plain"
            button-color="black"
            v-bind:paymentRequest="paymentRequest"
            v-on:loadpaymentdata="onLoadPaymentData"
            v-on:error="onError"
          ></google-pay-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import '@google-pay/button-element'

const paymentRequest = {
  apiVersion: 2,
  apiVersionMinor: 0,
  allowedPaymentMethods: [
    {
      type: 'CARD',
      parameters: {
        allowedAuthMethods: ['PAN_ONLY', 'CRYPTOGRAM_3DS'],
        allowedCardNetworks: ['MASTERCARD', 'VISA']
      },
      tokenizationSpecification: {
        type: 'PAYMENT_GATEWAY',
        parameters: {
          gateway: 'example',
          gatewayMerchantId: 'exampleGatewayMerchantId'
        }
      }
    }
  ],
  merchantInfo: {
    merchantId: 'BCR2DN4TYHQ2ZQ2H',
    merchantName: 'VuePay'
  },
  transactionInfo: {
    totalPriceStatus: 'FINAL',
    totalPriceLabel: 'Total',
    totalPrice: '100.00',
    currencyCode: 'MXN',
    countryCode: 'ES'
  }
}

const onLoadPaymentData = (event) => {
  console.log('load payment data', event.detail)
}

const onError = (event) => {
  console.error('error', event.error)
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.example {
  margin: 5px;
  display: flex;
  flex-direction: row;
}

.example > .title {
  width: 250px;
  align-items: center;
  display: inherit;
}

.example > .demo {
  flex: 1 0 0;
}

.example > .demo > * {
  margin: 1px;
}
</style>
