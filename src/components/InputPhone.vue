<template>
  <div style="display: flex; flex-direction: column;">
    <input :type="type" id="input_phone" ref="input" :class="{novalid: novalidity}" style="width: 179px" @input="checkValidation()" v-model="note" :placeholder="placeholder" required/>
    <div class="error_note">{{ texterror }}</div>
  </div>
</template>

<script>
let Reg = new RegExp(/^\+?(\d{1,3})?[- .]?\(?(?:\d{2,3})\)?[- .]?\d\d\d[- .]?\d\d\d\d$/)
export default {
  name: 'InputPhone',
  data () {
    return {
      type: 'tel',
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
