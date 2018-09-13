<template>
  <div id="app">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-6">
          <component v-bind:is="currentComponent" v-bind:profile="profile" v-on:complete="showSummary($event)"></component>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Summary from './components/Summary';
import ProfileForm from './components/ProfileForm';

export default {
  name: 'app',
  components: {
    Summary,
    ProfileForm
  },
  data() {
    return {
      profile: {
        fullName: null,
        birthDate: null,
        skills: [],
        email: null,
        tel: null,
      },
      isFormComplete: false
    }
  },
  computed: {
    currentComponent() {
      return this.isFormComplete ? Summary : ProfileForm;
    } 
  },
  methods: {
    showSummary(complete) {
      this.isFormComplete = complete;
    }
  }
}
</script>

<style>
  .page-title {
    text-align: center;
  }
</style>
