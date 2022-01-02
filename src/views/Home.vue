<template>
  <form @submit.prevent="procesarFormulario">
    <Input :tarea="tarea" />
  </form>

  <ListaTareas />
</template>

// ************************* // ********SCRIPT*********** //
*************************
<script>
import Input from '../components/Input'
import ListaTareas from '../components/ListaTareas'
import { mapActions } from 'vuex'
const shortid = require('shortid')

export default {
  name: 'Home',
  components: {
    Input,
    ListaTareas,
  },
  data() {
    return {
      tarea: {
        id: '',
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0,
      },
    }
  },
  methods: {
    ...mapActions(['setTareas']),
    procesarFormulario() {
      // console.log(this.tarea)
      if (this.tarea.nombre.trim() === '') {
        // console.log('Campo vacio')
        return
      }
      // console.log('Campo NO vacio')

      //  Generar id
      this.tarea.id = shortid.generate()
      // (this.tarea.id)

      // Enviar datos
      this.setTareas(this.tarea)

      // Limpiar datos
      this.tarea = {
        id: '',
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0,
      }
    },
  },
}
</script>
