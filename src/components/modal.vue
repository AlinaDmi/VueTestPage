<template>
  <div>
      <h1 class="my-2">Налоговый вычет </h1>
      <p>
          Используйте налоговый вычет, чтобы погасить ипотеку досрочно. Размер налогового вычета составляетне более 13% от своего официального годового дохода. 
      </p>
      <form v-on:submit.prevent="handleCount">
        <div class="form-group my-0">
         <label for="salary"><h4>Ваша зарплата в месяц</h4></label>
         <input type="text" class="input-form" v-model="salary" id="salary" placeholder="Введите данные">
        <p id="error">{{error}}</p>
        </div>
              
        <button  class="btn btn-link btn-anchor d-flex justify-content-end count-btn p-0" >
                Рассчитать
        </button> 
      </form>
      <div v-if="!error && annual">
        <h4 class="my-2">Итого можно ввести в качестве досрочных:</h4>

       <ul>
          <li v-for="index in times" :key="index">
        

             <div class="checkbox-container">
                 <input type="checkbox" :id="'cb' + index">
                 <label v-bind:for="'cb' + index">{{annual}} в {{index}}-й год</label>
             </div>
          </li>
          <li>
            <div v-if="rest" class="checkbox-container">
                 <input type="checkbox" id="cb"> 
                 <label for="cb">{{rest}} в {{times+1}}-й год</label>
             </div>
          </li>
             </ul>
      </div>
      <b-container >
        <b-row>
            <b-col class="mx-0 px-0">
               <h4>Что уменьшаем?</h4> 
            </b-col>
            <b-col>
              <div class="radio-container">
          <input type="radio" name="reduce" id="platez" checked="checked">
          <label for="platez">Платёж</label>

          <input type="radio" name="reduce" id="srok">
          <label for="srok">Срок</label>
            </div>
            </b-col>
        </b-row>
        </b-container>
        <div class="btn-container">
            <button class="btn-modal">Добавить</button>
        </div>
  </div>    
</template>

<script>
export default {
    data() {
    return {
      salary:'',
      annual:'',
      times:'',
      rest:'',
      error:''
    };
  },
    methods: {
        handleCount(){
             this.annual=''
             this.times=''
             this.rest=''
            this.error=''
            if(this.salary>0){
                this.annual = this.salary*12*0.13;
                 this.times = Math.floor(260000/this.annual)
                this.rest = 260000-(this.annual*this.times)
            } else{
                this.error = 'Поле обязательно должно быть заполнено и зарплата не может быть отрицательной'
            }
            
        }
    }
}
</script>

<style scoped>
    h1{
        font-size: 18px;
    }
    p {
        color:#808080;
        font-size: 16px;
    }
    #error{
        color: #EA0029;
        font-size: 12px;
    }
    h4{
        font-size: 14px;
    }
    li{
        list-style-type: none;
    }

    ul {
    margin-left: 0; /* Отступ слева в браузере IE и Opera */
    padding-left: 0; /* Отступ слева в браузере Firefox, Safari, Chrome */
   }

</style>