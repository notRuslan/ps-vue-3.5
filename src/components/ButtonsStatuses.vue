<script setup>

import SmallOKIcon from "../icons/SmallOKIcon.vue";
import SmallNotOKIcon from "../icons/SmallNotOKIcon.vue";
import StatusButton from "./Statuses/StatusButton.vue";

const emit = defineEmits(['clickNotOk', 'clickOk']);

function clickNotOk(){
  emit('clickNotOk');
}
function clickOk(){
  emit('clickOk');
}

</script>

<template>
 <div>
   <StatusButton @click="clickNotOk()"><SmallNotOKIcon /></StatusButton>
   <StatusButton  @click="clickOk()"><SmallOKIcon/></StatusButton>
 </div>

</template>

<style scoped>

</style>
