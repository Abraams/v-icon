<script setup>
import VIcon from './components/VIcon.vue'
import VBtn from './components/VBtn.vue'
import AppleIcon from '@reg-design/ds-static-icons/ds-icons/__apple'
import LinkExternal from '@reg-design/ds-static-icons/ds-icons/__link-external' // multipath icon
</script>

<template>
    <div>
        <VIcon
            width="200"
            height="200"
            color="#333"
            :icon="AppleIcon"
        />
    </div>
  <div>
      <VBtn
          color="red"
          block
      >
          <template #icon="attrs">
              <VIcon
                  v-bind="attrs"
                  width="16"
                  height="16"
                  :icon="AppleIcon"
              />
          </template>

          <span>
              My Button
          </span>
      </VBtn>


      <VBtn
          color="green"
          block
          :icon="LinkExternal"
      >
          <span> My Button 2 </span>
      </VBtn>

      <VBtn
          color="blue"
          block
          :icon="AppleIcon"
          icon-position="left"
      >
          <span> My Button 3 </span>
      </VBtn>
  </div>
</template>

