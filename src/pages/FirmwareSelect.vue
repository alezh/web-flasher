<script setup>
import {store} from '../js/state';
import HoverCard from '../components/HoverCard.vue';

const emit = defineEmits(['onClick']);

// Set firmware and targetType in state store, then update page to pages selection page
function setFirmware(firmware, targetType) {
  store.firmware = firmware;
  store.targetType = targetType;
  emit('onClick');
}
</script>

<template>
  <div class="containerMain">
    <div class="containerHeader">
      <VCardTitle>主控 固件</VCardTitle>
      <VCardSubtitle>Controlled or controlling... we got you covered!</VCardSubtitle>
    </div>
    <VRow>
      <VCol md="6">
        <HoverCard min-height="100%" @click="setFirmware('firmware', 'tx')"
                    image="transmitter_6275858.png" hover-image="transmitter_6276574.png"
                    title="高频头"
                    text="Update your external transmitter module, JR Bay (Micro) or Nano module; or an internal module
                    built into your radio handset."/>
      </VCol>
      <VCol md="6">
        <HoverCard min-height="100%" @click="setFirmware('firmware', 'rx')"
                    image="reciever_6276002.png" hover-image="reciever_6276814.png"
                    title="接收机"
                    text="Serial connected and PWM receivers alike can be updated here."/>
      </VCol>
    </VRow>
  </div>
  <div class="containerMain">
    <div class="containerHeader">
      <VCardTitle>背包 固件</VCardTitle>
      <VCardSubtitle>Wireless control of <i>all</i> the things!</VCardSubtitle>
    </div>
    <VRow>
      <VCol md="3">
        <HoverCard min-height="100%" @click="setFirmware('backpack', 'txbp')"
                    image="backpack_723137.png" hover-image="backpack_723278.png"
                    title="发射模块"
                    text="Built in to most transmitters, it communicates with the other backpacks or via WiFi to a computer
                    running Mission Planner (or other) for MAVLink craft."/>
      </VCol>
      <VCol md="3">
        <HoverCard min-height="100%" @click="setFirmware('backpack', 'vrx')"
                    image="vr-glasses_8736938.png" hover-image="vr-glasses_8737003.png"
                    title="视频接受"
                    text="A built-in VRx backpack like the HDZero goggles backpack, or the SkyZone ELRS backpack; or a
                    DIY solution connected to a VRx allows you to always have your goggles on the right channel."/>
      </VCol>
      <VCol md="3">
        <HoverCard min-height="100%" @click="setFirmware('backpack', 'aat')"
                    image="satellite_2637312.png" hover-image="satellite_2637314.png"
                    title="天线追踪"
                    text="Flying long-range and need your antenna pointed in just the right direction? This is the backpack
                    for you!"/>
      </VCol>
      <VCol md="3">
        <HoverCard min-height="100%" @click="setFirmware('backpack', 'timer')"
                    image="stopwatch_4354897.png" hover-image="stopwatch_4355918.png"
                    title="比赛计时器"
                    text="Connects to the RotorHazard race timing system and sends OSD message with lap times and current
                    place during the race so you always know where you're placed."/>
      </VCol>
    </VRow>
  </div>
</template>

<style scoped>
.v-card-title {
  padding: 0;
  font-size: 1.5rem;
  font-weight: 600;
  color: #242527;
}

.v-card-subtitle {
  padding: 0;
  font-size: 1rem;
  color: #242527;
}
</style>