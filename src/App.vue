<template>
  <div id="app">
    <div id="error" class="error">

    </div>
    <div class="container">

      <h1>Заполни анкету</h1>

      <form id="main_form">
        <div class="flexs">
          <div class="col-left">
            <fieldset>
              <legend>Введите ФИО</legend>
              <div class="flexs-inputs">
                <InputName
                  v-for="el in elements"
                  :key="el.id"
                  :placeholder="el.placeholder"
                />
              </div>
            </fieldset>
            <fieldset>
              <legend>Назовите возраст и пол</legend>
              <InputAge
                :placeholder="age.placeholder"
              />
              <div class="choose-gender">
                <input type="radio" id="radio1" class="gender" name="gender"><label for="radio1">Мужской</label>
                <input type="radio" id="radio2" class="gender" name="gender"><label for="radio2">Женский</label>
              </div>
            </fieldset>
            <fieldset>
              <legend>Укажите номер телефона</legend>
              <InputPhone
                :placeholder="phone.placeholder"
              />
            </fieldset>
            <fieldset>
              <legend>Укажите телосложение</legend>
              <input type="number" class="number" min="0" max="300" placeholder="Рост">
              <input type="number" class="number" min="0" max="300" placeholder="Вес">
            </fieldset>
            <fieldset>
              <legend>Выберите другие физические характеристики</legend>
              <select name="eyes">
                <option>Цвет глаз</option>
                <option>Карие</option>
                <option>Голубые</option>
                <option>Серые</option>
                <option>Зеленые</option>
              </select>
              <select name="hair">
                <option>Цвет волос</option>
                <option>Блонд</option>
                <option>Шатен</option>
                <option>Рыжий</option>
                <option>Русый</option>
                <option>Брюнет</option>
                <option>Седой</option>
              </select>
              <div class="choose-hand">
                <input type="checkbox" id="check-hand" class="check-hand" name="check-hand"><label for="check-hand"> Я - левша</label>
              </div>
            </fieldset>
            <fieldset>
              <legend>Загрузите фотографию</legend>
              <label for="file-upload">
                <div class="block-upload">
                  <div class="circle-upload"></div>
                  <input type="file" id="file-upload">
                  Загрузить
                </div>
              </label>
            </fieldset>
          </div>
          <div class="col-right">
            <fieldset>
              <legend style="text-align: right">Расскажите о себе</legend>
              <textarea>
                    </textarea>
            </fieldset>
          </div>

          <div class="low-row">
            <div class="low-row-center">
              <button class="send" type="submit">
                <div class="circle-send">
                </div>
              </button>
            </div>
          </div>
        </div>
      </form>

    </div>
  </div>
</template>

<script>
import InputName from './components/InputName'
import InputAge from './components/InputAge'
import InputPhone from './components/InputPhone'
export default {
  name: 'app',
  data () {
    return {
      elements: [
        { index: 1, id: 'lastName', placeholder: 'Фамилия' },
        { index: 2, id: 'firstName', placeholder: 'Имя' },
        { index: 3, id: 'thirdname', placeholder: 'Отчество' }
      ],
      age: {
        index: 4,
        id: 'ageValue',
        placeholder: 'Возраст'
      },
      phone: {
        index: 5,
        id: 'phoneValue',
        placeholder: 'Номер телефона'
      }
    }
  },
  components: {
    InputName,
    InputAge,
    InputPhone
  }
}

</script>

<style lang="css" src="./pages/styles/style.css"></style>
