<template>
  <div>
    <label>{{customLabel}}</label>
    <input type="range" v-bind="$attrs" :class="inputClasses"     
    :value="valor" @change="atualizar">
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  model:{
      prop: 'valor',
      event: 'change'
  },
  props: {
    label: String,
    valor: [Number, String],
    inputClasses: [String, Object, Array]
  },
 // data() {
 //   return { valorAtual: this.valor || this.$attrs.min}
 // },//comentado porque não atualizava a label no formulario
  computed: {
    customLabel() {
     // return `${this.label} (R$ ${this.valorAtual})`; comentado porque não atualizava a label no formulario
     return `${this.label} (R$ ${this.valor || this.$attrs.min})`;
    }
  },
  methods: {
    atualizar(event ) {
        const valor = event.target.value
        this.$emit('change',valor)
        //this.valorAtual = valor
    }
  },
  created() {}
};
</script>
