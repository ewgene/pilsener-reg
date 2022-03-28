<template>
  <div id="registration">

    <h3>
      <span class="arrow">
        <i class="fa-arrow-left"></i>
      </span> Регистрация 
      <span class="arrow"></span>
    </h3>

    <div class="registration-form">

      <label for="phone_number" class="phone_label">
        Введите номер телефона
      </label>
      <div class="phone_input">
        <input
            type="tel"
            id="phone_number"
            v-number-only
            v-model="phoneNumber"
            />
      </div>
      <div class="checkbox">
        <input
          type="checkbox"
          class="agree"
          id="agree"
          v-model="agree"
          />
        <span class="checkmark"></span>
      </div>
      <label for="agree" 
        class="disclaimer"
        v-html="disclaimer">
      </label>
    </div>
    <div
      class="check_button">
      Проверить номер  
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  directives: {
    'number-only': {
      bind (el) {
        function checkValue (event) {
          event.target.value = event.target.value.replace(/[^0-9]/g, '')
          if (event.charCode >= 48 && event.charCode <= 57) {
            return true
          }
          event.preventDefault()
        }
        el.addEventListener('keypress', checkValue)
      }
    }
  },
/*  props: {
    isLogged
  },*/
  data () {
    return {
      countryCode: {
        RU: "+7"
      },
      currentCode: "+7",
      phoneNumber: null,
      agree: false,
      disclaimer: "Продолжая, я соглашаюсь с <span class='blue'>Пользовательским соглашением</span> и с обработкой моей персональной информации на условиях <span class='blue'>Политики конфиденциальности</span>."
    }
  }
}
</script>

<style lang="scss">

$char-w: 1ch;
$gap: .5*$char-w;
$n-char: 10;
$in-w: $n-char*($char-w + $gap);

#registration {
  width: 100%;

  .registration-form {
    padding: 23px;

    .phone_input {
      margin-bottom: 75px;
    }
    
    .phone_label {
      font-style: normal;
      font-weight: 500;
      font-size: 12px;
      line-height: 140%;
      display: block;
      text-align: center;
      letter-spacing: 0.03em;
      color: #8D8D92;
    }
    #phone_number {
      font-family: 'Cousine', monospace;
      font-size: 26px;
      font-weight: 700;
      text-align: left;
      width: 13ch;
      border: 0;
      background: repeating-linear-gradient(
        90deg,
        dimgrey 0, 
        dimgrey $char-w, 
        transparent 0, 
        transparent $char-w + $gap
        ) 0 100%
        / #{$in-w - $gap} 2px no-repeat;
        letter-spacing: $gap;

        &:focus {
          outline: none;
        }
    }
  }
}
.checkbox {
    display: block;
    position: relative;
    cursor: pointer;
    font-size: 23px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;

    .agree {
      position: absolute;
      top: 0;
      left: 0;
      opacity: 0;
      cursor: pointer;
      height: 23px;
      width: 23px;
      z-index: 100;

      &:hover ~ .checkmark {
          background-color: #ccc;
      }
      &:checked ~ .checkmark {
        background-color: #23A67E;

        &::after {
          display: block;
        }
      }
    }

    .checkmark {
      position: absolute;
      top: 0;
      left: 0;
      height: 23px;
      width: 23px;
      background-color: #eee;

      &::after {
        content: "";
        position: absolute;
        display: none;
        left: 9px;
        top: 5px;
        width: 5px;
        height: 10px;
        border: solid white;
        border-width: 0 3px 3px 0;
        -webkit-transform: rotate(45deg);
        -ms-transform: rotate(45deg);
        transform: rotate(45deg);
      }
    }
}
.disclaimer {
  display: block;
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 21px;
  letter-spacing: 0.02em;
  text-align: left;
  padding: 0 0 0 30px;

  .blue {
    color:#5da6eb;
  }
}
.check_button {
  height: 38px;
  width: 335px;
  background: #23A67E;
  border-radius: 5px;
  font-size: 16px;
  color: #fff;
  text-align: center;
  display: block;
  margin: 0 auto;
  padding-top: 16px;
}
</style>
