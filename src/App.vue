<template>
  <div class="display">
    <input class="value" v-model='visualValue'/>
    <div class="buttons">
      <my-button color="darkgray" @clickBtn="clickBtn" value="C">C</my-button>
      <my-button color="darkgray" @clickBtn="clickBtn" value="+/-">+/-</my-button>
      <my-button color="darkgray" value="%" @clickBtn="clickBtn">%</my-button>
      <my-button color="orange" value="/" @clickBtn="clickBtn" ref="action" :disabled="disabledOn">/</my-button>
      <my-button color="fairgray" value="7" @clickBtn="clickBtn">7</my-button>
      <my-button color="fairgray" value="8" @clickBtn="clickBtn">8</my-button>
      <my-button color="fairgray" value="9" @clickBtn="clickBtn">9</my-button>
      <my-button color="orange" value="*" @clickBtn="clickBtn" ref="action" :disabled="disabledOn">x</my-button>
      <my-button color="fairgray" value="4" @clickBtn="clickBtn">4</my-button>
      <my-button color="fairgray" value="5" @clickBtn="clickBtn">5</my-button>
      <my-button color="fairgray" value="6" @clickBtn="clickBtn">6</my-button>
      <my-button color="orange" value="-" @clickBtn="clickBtn" ref="action" :disabled="disabledOn">-</my-button>
      <my-button color="fairgray" value="1" @clickBtn="clickBtn">1</my-button>
      <my-button color="fairgray" value="2" @clickBtn="clickBtn">2</my-button>
      <my-button color="fairgray" value="3" @clickBtn="clickBtn">3</my-button>
      <my-button color="orange" value="+" @clickBtn="clickBtn" ref="action" :disabled="disabledOn">+</my-button>
      <my-button color="fairgray" class="btn-long" value="0" @clickBtn="clickBtn">0</my-button>
      <my-button color="fairgray" value="." @clickBtn="clickBtn" ref="action" :disabled="disabledOn">.</my-button>
      <my-button color="fairgray" value="=" @clickBtn="clickBtn">=</my-button>
  </div>
  </div>
</template>

<script>
import MyButton from './components/MyButton'
export default {
  data(){
    return {
      visualValue: '',
      finalValue: 0,
      disabledOn: false
    }
  },
  components: {
    MyButton
  },
  methods: {
    clickBtn(value){
      if(value=='+' || value=='-' || value=='/' || value=='*' || value=='.'){
        if(this.visualValue){
          console.log('hello!');
          this.disabledOn = true;
          this.visualValue += value;
        }
      }
      else if(isFinite(value)){
        this.disabledOn = false;
        this.visualValue += value
      }
      else if(value == 'C'){
        this.visualValue = this.visualValue.slice(0, -1);
        this.disabledOn = false;
      }
      else if(value=='%'){
        this.visualValue += value;
      }
      else if(value == '='){
        this.visualValue = eval(this.visualValue)
      }
    }
  }
}
</script>

<style>
  *{
    padding: 0;
    margin: 0;
  }
  .display{
    display: flex;
    flex-direction: column;
    height: 524px;
    justify-content: flex-end;
    width: calc(64px * 4 + 12px * 3);
    background-color: black;
    padding: 20px;
    border-radius: 15px;
  }
  .value{
    text-align: end;
    color: white;
    font-size: 48px;
    border: none;
    background: none;
    display: flex;
    flex-wrap: wrap;
  }
  .buttons{
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    align-items: flex-end;
    width: calc(64px * 4 + 12px * 3);
  }
  .btn-long{
    flex: 2;
  }
</style>