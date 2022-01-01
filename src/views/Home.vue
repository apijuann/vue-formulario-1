<template>
  <form @submit.prevent="procesarFormulario">
    <!-- Input form -->
    <input 
      type="text"
      class="form-control my-2"
      placeholder="Enter a name"
      v-model.trim="tarea.nombre"
      >
      <!-- End of input form -->
    <!-- Checkbox -->
    <div class="form-check form-check-inline">
      <input 
        type="checkbox"
        id="check-1"
        class="form-check-input"
        v-model="tarea.categorias"
        value="javascript"
        >
      <label for="check-1" class="form-check-label">Javascript</label>
    </div>

    <div class="form-check form-check-inline">
      <input 
        type="checkbox"
        id="check-2"
        class="form-check-input"
        v-model="tarea.categorias"
        value="node js"
        >
      <label for="check-2" class="form-check-label">Node js</label>
    </div>
    <!-- End of checkbox -->
    <!-- Radio -->
      <div class="mt-2">
        <div class="form-check form-check-inline">
          <input 
            class="form-check-input" 
            type="radio" 
            id="radio-1" 
            value="urgent"
            v-model="tarea.estado"
            >
          <label class="form-check-label" for="radio-1">Urgent</label>
        </div>

        <div class="form-check form-check-inline">
          <input 
            class="form-check-input" 
            type="radio" 
            id="radio-2" 
            value="relax"
            v-model="tarea.estado"
            >
          <label class="form-check-label" for="radio-2">Relax</label>
        </div>
      </div>
    <!-- End of radio -->
    <!-- Input number -->
      <div class="mt-2">
        <input 
          type="number"
          class="form-control"
          v-model.number="tarea.numero"
          >
      </div>
    <!-- End of input number -->
    <!-- BOTON PROCESAR -->
    <div class="mt-2">
      <button 
        class="btn btn-dark btn-block" 
        type="submit"
        :disabled="bloquear"
      >
      Precesar</button>
    </div>
    <!-- End boton procesar -->
    </form>

  <hr>
  
  <p>{{tarea}}</p>
</template>


// *************************
// ********SCRIPT***********
// *************************
<script>

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      tarea: {
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
  methods: {
    procesarFormulario() {
      console.log(this.tarea)
      if (this.tarea.nombre.trim()==="") {
        console.log('Campo vacio')
        return
      }
      console.log('Campo NO vacio')
      // Enviar datos


      // Limpiar
      this.tarea = {
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
  computed: {
    bloquear(){
      return this.tarea.nombre.trim()==="" ? true : false
    }
  }
}
</script>
