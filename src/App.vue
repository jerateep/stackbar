<template>
  <StackedBar :data="data" />
</template>
<script>
  import { defineComponent, ref,watch, onMounted } from "vue";
  import StackedBar from './components/StackedBar/StackedBarComponent.vue'
  export default defineComponent({
    components: {
      StackedBar,
    },
    setup(){
      const data = ref([
        {
          title: 'First',
          value: 19,
          percent: 19,
          color: '#007bff'
        },
        {
          title: 'Second',
          value: 36,
          percent: 36,
          color: '#20c997'
        },
        {
          title: 'Third',
          value: 45,
          percent: 45,
          color: '#f28b8c'
        }
      ])
      return{
        data
      }
    }
  })
</script>