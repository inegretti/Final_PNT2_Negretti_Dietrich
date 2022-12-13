<template >

  <section class="src-components-formulario">
    <div class="jumbotron">
    <h1>Conversor a Dolar</h1>
    <hr>
    <hr>
    <br>
    <vue-form :state="formState">
 
         <br>
          <validate tag="label">
            <span>Monto: $ </span>
            <input v-model="formData.monto" name="monto" type="number" required :min="1"/>
            <field-messages name="monto" show="$dirty">
              <div slot="required">Complete el campo</div>
            </field-messages>
          </validate>
          <br>
         <br>

          <br>
          <validate tag="label">
            <span>Precio Dolar: $ </span>
            <input v-model="formData.precio" name="precio" type="number" required :min="1"/>
            <field-messages name="precio" show="$dirty">
              <div slot="required">Complete el campo</div>
            </field-messages>
          </validate>
          <br>
         <br>
  </vue-form>
  <hr>
  <span>Monto en U$D {{calcularMonto()}}</span> 
  
    </div>
  </section>

</template>

<script >

  export default  {
    name: 'src-components-formulario',
    props: [],
    mounted () {
      
    },
    data () {
      return {
        formState:{},
        formData:this.getDataInicial(),
        Min:3,
        Max:15,
        montoDolar:0
      }
    },
    methods: {
      enviar(){
        this.formData= this.getDataInicial()
        this.formState._reset()
      },
      getDataInicial(){
         return {
          monto:0,
          precio:0
         }
      },
      calcularMonto(){
        let resp=0;
        this.montoDolar=resp
        if(this.formData.monto!=0 && this.formData.precio!=0){
            resp=this.formData.monto/this.formData.precio; 
        }
        return resp
      }
      

    },
    computed: {

    
 }
}



</script>

<style scoped lang="css">
  .src-components-formulario {

  }
  .jumbotron{
    background-color: green;
    color: black;
  }
  hr{
    background-color: black;
  }
</style>
