<template>
  <div style="display: flex; flex-direction: column;">
    <input :type="type" ref="input" :class="{novalid: novalidity}" class="symbols" @input="checkValidation()" v-model="note" :placeholder="placeholder"  required/>
    <div class="error_note">{{ texterror }}</div>
  </div>
</template>

<script>
let Reg = new RegExp(/[0-9]/)
export default {
  name: 'InputName',
  data () {
    return {
      type: 'text',
      maxlength: 10,
      novalidity: false,
      note: '',
      texterror: ''
    }
  },
  props: ['index', 'id', 'placeholder'],
  methods: {
    checkValidation () {
      if (this.note.length >= 10) {
        this.novalidity = true
        this.texterror = 'Превышено допустимое количество символов - ' + this.maxlength + ' в поле ' + this.placeholder
      } else if (this.note.length === 0) {
        this.novalidity = true
        this.texterror = 'Поле ' + this.placeholder + ' не должно быть пустым'
      } else if (Reg.test(this.note)) {
        this.novalidity = true
        this.texterror = 'Поле ' + this.placeholder + ' не может содержать цифр'
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
