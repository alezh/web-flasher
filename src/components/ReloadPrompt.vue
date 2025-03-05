<script setup>
import { useRegisterSW } from 'virtual:pwa-register/vue'

const {
  offlineReady,
  needRefresh,
  updateServiceWorker,
} = useRegisterSW()

function close() {
  offlineReady.value = false
  needRefresh.value = false
}
</script>

<template>
  <VBanner v-if="offlineReady || needRefresh" class="pwa-toast" elevation="1" color="info">
    <VBannerText v-if="offlineReady">
      应用程序已准备好离线工作
    </VBannerText>
    <VBannerText v-else>
      有新内容可用，更新至最新?
    </VBannerText>
    <template #actions>
      <VBtn v-if="needRefresh" @click="updateServiceWorker()">更新</VBtn>
      <VBtn @click="close()">取消</VBtn>
    </template>
  </VBanner>
</template>

<style>
.pwa-toast {
  position: fixed;
  right: 0;
  bottom: 0;
  margin: 16px;
  width: unset;
  z-index: 99999;
  border-radius: 0.5rem;
}
</style>