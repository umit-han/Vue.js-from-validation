<template>
  <div class="content">
    <div class="row">
      <div class="col-12">
        <div class="card-form">
          <form action="">

            <fieldset class="card-form__group">
              <label class="card-form__label" :class="{'card-form__label--error' : $v.firstName.$error}">First Name</label>
              <input
                @blur="$v.firstName.$touch()"
                v-model="firstName" 
                type="text"
                :class="{'card-form__input--error' : $v.firstName.$error}"  
                class="card-form__input" 
                id="firstName">
              <small v-if="!$v.firstName.required" class="form-text text-danger" :class="{'d-none': !$v.firstName.$error}"> This field is required.</small>
              <small v-if="!$v.firstName.minLength" class="form-text text-danger" :class="{'d-none': !$v.firstName.$error}">Your name must be at least 3 letters.</small>
            </fieldset>

            <fieldset class="card-form__group">
              <label class="card-form__label" :class="{'card-form__label--error' : $v.lastName.$error}">Last Name</label>
              <input 
                @blur="$v.lastName.$touch()"
                v-model="lastName"
                type="text"
                :class="{'card-form__input--error' : $v.lastName.$error}" 
                class="card-form__input" 
                id="lastName">
              <small v-if="!$v.lastName.required" class="form-text text-danger" :class="{'d-none': !$v.lastName.$error}"> This field is required.</small>
              <small v-if="!$v.lastName.minLength" class="form-text text-danger" :class="{'d-none': !$v.lastName.$error}">Your surname must contain at least 2 letters.</small>
            </fieldset>

            <fieldset class="card-form__group">
              <label class="card-form__label" :class="{'card-form__label--error' : $v.age.$error}">Age</label>
              <input
                @blur="$v.age.$touch()" 
                v-model="age"
                type="text"
                :class="{'card-form__input--error' : $v.age.$error}"  
                class="card-form__input" 
                id="age">
              <small v-if="!$v.age.required" class="form-text text-danger" :class="{'d-none': !$v.age.$error}"> This field is required.</small>
              <small v-if="!$v.age.numeric" class="form-text text-danger" :class="{'d-none': !$v.age.$error}">Your age should consist of numbers.</small>
              <small v-if="!$v.age.between" class="form-text text-danger" :class="{'d-none': !$v.age.$error}">Your vaccine should be between {{$v.age.$params.between.min}} and {{$v.age.$params.between.max}} years old.</small>
            </fieldset>

            <fieldset class="card-form__group">
              <label class="card-form__label" :class="{'card-form__label--error' : $v.email.$error}">E-mail</label>
              <input
                @blur="$v.email.$touch()" 
                v-model="email"
                type="email"
                :class="{'card-form__input--error' : $v.email.$error}"  
                class="card-form__input" 
                id="mail">
              <small v-if="!$v.email.required" class="form-text text-danger" :class="{'d-none': !$v.email.$error}"> This field is required.</small>
              <small v-if="!$v.email.email" class="form-text text-danger" :class="{'d-none': !$v.email.$error}">Please enter a valid e-mail address.</small>
            </fieldset>

            <fieldset class="card-form__group">
              <label class="card-form__label" :class="{'card-form__label--error' : $v.phone.$error}">Phone Number</label>
              <input
                @blur="$v.phone.$touch()"
                v-model="phone" 
                type="text"
                :class="{'card-form__input--error' : $v.phone.$error}"  
                class="card-form__input" 
                id="phone">
              <small v-if="!$v.phone.required" class="form-text text-danger" :class="{'d-none': !$v.phone.$error}"> This field is required.</small>
              <small v-if="!$v.phone.numeric" class="form-text text-danger" :class="{'d-none': !$v.phone.$error}"> Your phone number must consist of numbers.</small>
              <small v-if="!$v.phone.maxLength" class="form-text text-danger" :class="{'d-none': !$v.phone.$error}">Your phone number must contain up to {{$v.phone.$params.maxLength.max}} letters.</small>
            </fieldset>

            <fieldset class="card-form__group">
              <label class="card-form__label" :class="{'card-form__label--error' : $v.password.$error}">Password</label>
              <input
              @blur="$v.password.$touch()"
              v-model="password"
              type="password"
              :class="{'card-form__input--error' : $v.password.$error}"  
              class="card-form__input" 
              id="password">
              <small v-if="!$v.password.required" class="form-text text-danger" :class="{'d-none': !$v.password.$error}"> This field is required.</small>
              <small v-if="!$v.password.minLength" class="form-text text-danger" :class="{'d-none': !$v.password.$error}"> Your password must be at least {{$v.password.$params.minLength.min}} characters. </small>
              <small v-if="!$v.password.maxLength" class="form-text text-danger" :class="{'d-none': !$v.password.$error}"> Your password must contain a maximum of {{$v.password.$params.maxLength.max}} characters. </small>
            </fieldset>

            <fieldset class="card-form__group">
            <label class="card-form__label" :class="{'card-form__label--error' : $v.confirmPassword.$error}">Confirm Password</label>
              <input
                @blur="$v.confirmPassword.$touch()"
                v-model="confirmPassword" 
                type="password"
                :class="{'card-form__input--error' : $v.confirmPassword.$error}" 
                class="card-form__input" 
                id="confirmPassword">
              <small v-if="!$v.confirmPassword.required" class="form-text text-danger" :class="{'d-none': !$v.confirmPassword.$error}"> This field is required.</small>
              <small v-if="!$v.confirmPassword.minLength" class="form-text text-danger" :class="{'d-none': !$v.confirmPassword.$error}"> Your password must be at least {{$v.confirmPassword.$params.minLength.min}} characters.</small>
              <small v-if="!$v.confirmPassword.maxLength" class="form-text text-danger" :class="{'d-none': !$v.confirmPassword.$error}"> Your password must contain a maximum of {{$v.confirmPassword.$params.maxLength.max}} characters. </small>
              <small v-if="!$v.confirmPassword.sameAsPassword" class="form-text text-danger" :class="{'d-none': !$v.confirmPassword.$error}">Your password does not match.</small>
            </fieldset>

            <fieldset class="card-form__group">
              <!-- <button class="btn btn-outline-success rounded-0" :disabled="$v.$invalid">Save</button> -->
              <button class="btn-save rounded-0" :disabled="$v.$invalid">Save</button>
            </fieldset>

          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import {required, email, minLength, maxLength, between, sameAs, numeric} from 'vuelidate/lib/validators'
export default {
  data() {
    return {
      firstName: null,
      lastName: null,
      age: null,
      phone: null,
      email: null,
      password: null,
      confirmPassword: null,

    }
  },

  validations: {
    firstName: {
      required,
      minLength: minLength(3)
    },

    lastName: {
      required,
      minLength: minLength(2)
    },

    age: {
      required,
      numeric,
      between: between(18, 70)
    },

    email: {
      required,
      email,
      // uniq : value => {
      //   return axios.get('url')
      //     .then(response =>{
      //       setTimeout(() => {
      //         return false
      //       }, 1000);
      //     })
      //   }
    },

    phone:{
      required,
      numeric,
      maxLength: maxLength(11)
    },

    password: {
      required,
      maxLength: maxLength(10),
      minLength: minLength(6)
    },

    confirmPassword: {
      required,
      maxLength: maxLength(10),
      minLength: minLength(6),
      sameAsPassword: sameAs('password')
    }

  }
}

</script>

<style lang="scss">

</style>
