<template>
    <div>
        <h1 class="page-title">Резюме</h1>
        <table valign="top">
            <tr>
                <th>ФИО:</th>
                <td>{{ profile.fullName }}</td>
            </tr>
            <tr>
                <th>Дата родждения:</th>
                <td>{{ profile.birthDate }}</td>
            </tr>
            <tr>
                <th>Навыки:</th>
                <td>
                    <TagList v-bind:tags="profile.skills"></TagList>
                </td>
            </tr>
            <tr>
                <th>Адрес электронной почты:</th>
                <td>{{ profile.email }}</td>
            </tr>
            <tr>
                <th>Номер телефона:</th>
                <td>{{ profile.tel }}</td>
            </tr>
        </table>
    </div>
</template>

<script>
import TagList from './TagList';

export default {
    name: 'Summary',
    props: ['profile'],
    components: {
        TagList
    }
}
</script>

<style scoped>
    table {
        width: 100%;
        margin: 0 auto;
        table-layout: fixed;
    }

    table td,
    table th {
        vertical-align: top;
        padding-left: 1rem;
        padding-right: 1rem;
    }

    table th {
        text-align: right;
    }

    ul {
        padding-left: 20px;
    }
</style>
