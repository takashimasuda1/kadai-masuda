<template>
  <div class="home">
    <hr>
    <h3>ペットの登録はボタンを押してください★</h3>
    <button @click="togglePetForm" class="btn btn-primary">ペット登録</button>
    <b-form @submit.prevent="handleSubmit" v-if="showPetForm">


        <b-form-group id="input-group-1" label="種類:" label-for="input-1">
        <b-form-select
          id="input-1"
          v-model="formData.species"
          :options="['cats', 'dogs']"
          required
        ></b-form-select>
      </b-form-group>


      <b-form-group id="input-group-2" label="ペット名:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="formData.name"
          required
          placeholder="ペット名を入力してください"
        ></b-form-input>
      </b-form-group>


        <b-form-group id="input-group-3" label="年齢:" label-for="input-3">
        <b-form-input
          id="input-3"
          type="number"
          v-model="formData.age"
          required
          placeholder="年齢を入力してください"
        ></b-form-input>
      </b-form-group> 

      <b-form-group id="input-group-4" label="ブリード:" label-for="input-4">
        <b-form-input
          id="input-4"
          v-model="formData.breed"
          required
          placeholder="例：柴犬"
        ></b-form-input>
      </b-form-group>    
      
      <b-form-group id="input-group-5" label="性別:" label-for="input-5">
        <b-form-input
          id="input-5"
          v-model="formData.gender"
          required
          placeholder="オス・メス"
        ></b-form-input>
      </b-form-group>  

      <b-form-group id="input-group-6" label="色:" label-for="input-6">
        <b-form-input
          id="input-6"
          v-model="formData.color"
          required
          placeholder="色を入力してください"
        ></b-form-input>
      </b-form-group>     

       <b-form-group id="input-group-7" label="体重 (kg):" label-for="input-7">
        <b-form-input
          id="input-7"
          type="number"
          v-model="formData.weight"
          required
          placeholder="体重を入力してください"
        ></b-form-input>
      </b-form-group>

       <b-form-group id="input-group-8" label="場所:" label-for="input-8">
        <b-form-input
          id="input-8"
          v-model="formData.location"
          required
          placeholder="場所を入力してください"
        ></b-form-input>
      </b-form-group>   

        <b-form-group id="input-group-9" label="連絡先:" label-for="input-9">
        <b-form-input
          id="input-9"
          type="number"
          v-model="formData.contact"
          required
          placeholder="連絡先を入力してください"
        ></b-form-input>
      </b-form-group>  


      <b-button type="submit" variant="primary">登録する</b-button>
      <b-button type="reset" variant="danger">リセット</b-button>
    </b-form>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'home',
  data() {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        breed: '',
        gender: '',
        color: '',
        weight: '',
        location: '',
        contact: 0,
        species: null
      }
    }
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm() {
      this.showPetForm = !this.showPetForm
    },
    handleSubmit() {
    const { species, name, age, breed, gender, color, weight, location, contact } = this.formData
    const payload = {
        species,
        pet: {
          name,
          age,
          breed,
          gender,
          color,
          weight,
          location,
          contact
        }
      }
      this.addPet(payload)

      //reset form after submit

      this.formData = {
        name: '',
        age: 0,
        breed: '',
        gender: '',
        color: '',
        weight: '',
        location: '',
        contact: 0,
        species: null
      }

      

    }
  }
}
</script>

