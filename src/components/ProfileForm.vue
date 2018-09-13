<template>
    <form @submit="checkForm">
        <template v-if="currentStep === 'personal'">
            <h1 class="page-title">Личные данные</h1>
            <div class="form-group">
                <label for="full-name">ФИО</label>
                <input v-model="profile.fullName" class="form-control" id="full-name" name="full-name" type="text">
            </div>
            <div class="form-group">
                <label for="birth-date">Дата рождения</label>
                <input v-model="profile.birthDate" class="form-control" id="birth-date" name="birth-date" type="date">
            </div>
        </template>
        <template v-if="currentStep === 'skills'">
            <h1 class="page-title">Профессиональные навыки</h1>
            <div class="form-group">
                <label for="skills">Навык или навыки:</label>
                <InputList v-model="profile.skills" id="skills" name="skills"></InputList>
                <TagList v-bind:tags="profile.skills"></TagList>
            </div>
        </template>
        <template v-if="currentStep === 'contacts'">
            <h1 class="page-title">Контакты</h1>
            <div class="form-group">
                <label for="email">E-mail</label>
                <input v-model="profile.email" class="form-control" id="email" name="email" type="email">
            </div>
            <div class="form-group">
                <label for="tel">Телефон</label>
                <input v-model="profile.tel" class="form-control" id="tel" name="tel" type="text">
            </div>
        </template>
        <button class="btn btn-info" @click="nextStep" v-if="!isLastStep" type="button">Далее</button>
        <button class="btn btn-success" @click="complete" v-else type="button">Завершить</button>
    </form>
</template>

<script>
import TagList from './TagList';
import InputList from './InputList';

export default {
    name: 'ProfileForm',
    props: ['profile'],
    components: {
        TagList,
        InputList
    },
    errors: [],
    data() {
        return {
            steps: ['personal', 'skills', 'contacts'],
            currentIndex: 0,
        }
    },
    computed: {
        currentStep() {
            return this.steps[this.currentIndex];
        },
        isLastStep() {
            return this.currentIndex >= this.steps.length - 1;
        }
    },
    methods: {
        nextStep() {
            this.currentIndex++;
        },
        complete() {
            this.$emit('complete', true);
        },
        checkForm(e) {
            e.preventDefault();

            for (var key in this.profile) {
                if (!this.profile[key] || !this.profile[key].length) {
                    console.log(key);
                    this.errors.push(key);
                }
            }
        }
    }
}
</script>
