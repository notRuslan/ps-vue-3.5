<script setup>
const {color = '#09BB00', size = 24} = defineProps({
  color: String, //#09BB00
  size: Number,
});
</script>

<template>
  <svg
      :style="{scale: size / 24}"
      class="status-icon" width="24" height="24" viewBox="0 0 21 20" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path fill-rule="evenodd" clip-rule="evenodd"
          d="M11.4693 13.308L11.2543 13.689H10.4143L10.1613 13.353C10.1463 13.33 8.6593 11.108 6.7373 9.892L6.1023 9.492L6.9043 8.224L7.5373 8.624C8.92231 9.499 10.0723 10.777 10.7503 11.63C11.8153 10.025 14.3093 6.682 18.1343 3.971C16.3473 1.709 13.5863 0.25 10.4873 0.25C5.1113 0.25 0.737305 4.624 0.737305 10C0.737305 15.376 5.1113 19.75 10.4873 19.75C15.8633 19.75 20.2373 15.376 20.2373 10C20.2373 8.263 19.7753 6.635 18.9763 5.221C14.1433 8.667 11.4983 13.257 11.4693 13.308Z"
          :fill="color"/>
  </svg>
</template>

<style scoped>

</style>
