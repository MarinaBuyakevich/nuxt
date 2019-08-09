<template>
  <div class="container" id="panel">
    <h2>Форма обратной связи</h2>
    <form id="contactForm" method="post">
      <div class="field-block">
        <label for="name">Ваше имя:</label>
        <input id="name" class="field" name="name" type="text" placeholder="Иванов Иван Иванович">
      </div>
      <div class="field-block">
        <label for="phone">Ваш телефон:</label>
        <input id="phone" class="field" name="phone" required type="text" placeholder="+7 (000) 000-00-00" @focus="changePhone()">
      </div>
      <div class="field-block">
        <input id="check" name="check" checked type="checkbox" @click="checkForm()">
        <span class="check-text">{{ msg }}</span>
      </div>
      <button id="send_form" class="button" @click="clickFunction()">{{ submit }}</button>
    </form>
  </div>
</template>

<script >

  export default {
    data () {
      return {
        msg: 'Согласен на обработку персональных данных',
        submit: 'Отправить',
        post: null,
        error: null
      }
    },
    methods:{
      clickFunction: function (){
        if ($('#phone').val() === ''){
          return false
        }
        alert('Thank you, the form has been submitted');
        this.checkForm();
      },
      checkForm: function () {
        if ($("#check").prop("checked")) {
          $('#send_form').attr('disabled', false);
           // alert('Thank you, the form has been submitted');
        } else {
          $('#send_form').attr('disabled', true);
        }
      },
      changePhone: function () {
        $('#phone').mask("+7(999)999-99-99");
      }

    },
  }
</script>
<style scoped>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  body {
    font-family: Arial, sans-serif;
    font-size: 16px;
    background-color: #fff;
  }

  .container {
    max-width: 500px;
    margin: 50px auto;
    padding: 20px;
    border-radius: 4px;
    background-color: #ebebeb;
    box-shadow: 0 0 3px #666;
  }

  h2, .field-block {
    margin-bottom: 20px;
  }

  .field-block label, .field-block .field {
    display: block;
    width: 100%;
  }

  .field-block label {
    margin-bottom: 8px;
    font-weight: bold;
  }

  .field-block .field {
    font-size: 16px;
    padding: 8px 12px;
    line-height: 1.5;
    border-radius: 4px;
    border: 1px solid #ccc;
    box-shadow: inset 0 1px 1px rgba(0,0,0,0.075);
    transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  }

  .field-block .field:focus {
    border-color: #66afe9;
    outline: 0;
    box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, .6);
  }

  .field-block {
    resize: vertical;
  }

  .check-text {
    font-size: 14px;
    vertical-align: top;
  }

  .button {
    cursor: pointer;
    font-size: 16px;
    padding: 6px 12px;
    margin-bottom: 5px;
  }
</style>
