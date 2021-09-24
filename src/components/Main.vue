<template>
  <div class="back d-flex justify-content-center" >
    <!-- Button trigger modal -->

  <button type="button" v-b-modal.modal-center class="btn-main my-auto" data-toggle="modal" data-target="#exampleModalCenter">
  Досрочный платёж
  </button>

  <b-modal hide-footer hide-header  id="modal-center" centered>
    <button @click="$bvModal.hide('modal-center')" class="close-thik" style="border: 0; background: transparent; float:right">
            <img src="@/assets/close.png" />
     </button>
    <Modal />
  </b-modal>
  </div>
  
</template>

<script>
import Modal from '@/components/modal.vue'
export default {
   components: {
    Modal
  }
}
</script>
  
<style>
  .b-modal{
    border-radius: 0px !important; 
  }

  #modal-center {
    border-radius: 0px !important; 
  }

</style>