<script setup>
import { InfoCircleOutlined, CloseOutlined } from "@ant-design/icons-vue";

defineProps({
  alertData: {
    type: Object,
    required: false,
    default() {
      return {
        show: true,
        state: "warning",
        message: "預設!",
      };
    },
  },
});

defineEmits(["closeAlert"]);
</script>

<template>
  <div
    v-show="alertData.show"
    class="alert flex items-center"
    :class="{
      'bg-warning': alertData.state === 'warning',
      'bg-error': alertData.state === 'error',
    }"
  >
    <div class="flex items-center justify-center text-xl">
      <info-circle-outlined />
    </div>
    <div class="flex-grow overflow-ellipsis text-center">
      {{ alertData.message }}
    </div>

    <div class="flex items-center justify-center">
      <close-outlined @click="$emit('closeAlert')" />
    </div>
  </div>
</template>
