<template>
  <section class="md:w-1/3 flex flex-col p-12">
  <!-- Profile Card -->
    <h3 class="font-bold font-lg">{{ formData.name }}</h3>
    <p class="mt-2">{{ formData.occupation }}</p>
  </section>
</template>

<script>
import eventBus from '../event-bus';  // Importamos al Bus de Eventos
export default {
  mounted() {
    eventBus.$on('profileUpdate', this.update)  //EventBus avisa cuando haya un ProfileUpdate
  },
  beforeDestroy() {
    eventBus.$off('profileUpdate', this.update)
  },
  methods: {
    update(formData) {
      this.formData = formData;
    }
  },
  data () {
    return {
      formData: {}
    }
  }
  // props: {                 // Ya no usamos prop porque la info ya no viene del padre
  //   formData: {
  //     type: Object,
  //     default() {
  //       return {}
  //     }
  //   }
  // }
}
</script>
