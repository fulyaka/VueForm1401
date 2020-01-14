<template>
  <div style="display: flex; flex-direction: column;">
    <input :type="type" id="input_age" ref="input" class="number" :class="{novalid: novalidity}"  @input="checkValidation()" v-model="note" :placeholder="placeholder" required/>
    <div class="error_note">{{ texterror }}</div>
  </div>
</template>

<script>

let Reg = new RegExp(/^[ 0-9]+$/)
export default {
  name: 'InputAge',
  data () {
    return {
      type: 'number',
      novalidity: false,
      note: '',
      texterror: ''
    }
  },
  props: ['index', 'id', 'placeholder'],
  methods: {
    checkValidation () {
      if (this.note === undefined) {
        this.novalidity = true
        this.texterror = 'Поле ' + this.placeholder + ' не может быть пустым'
      } else if (!Reg.test(this.note)) {
        this.novalidity = true
        this.texterror = 'Заполните поле ' + this.placeholder + ' корректно'
      } else {
        this.novalidity = false
        this.texterror = ''
      }
    }
  }
}

</script>

<style scoped>
  .novalid {
    border: 2px solid red;
    color: red
  }
  .error_note {
    color: red;
    margin-bottom: 10px;
    width: 219px;
    text-align: center;
  }
  .symbols {
    max-height: 22px;
  }

  @media screen and (max-width: 767px) {
    .error_note {
      width: 100%;
    }
  }

</style>
