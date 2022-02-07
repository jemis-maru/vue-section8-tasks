<template>
    <div>
        <form action="" @submit.prevent = "submitFun">
            <h2>Add friend</h2>
            <div>
                <label>Name: </label>
                <input type="text" v-model="formData.name" required>
            </div>
            <div>
                <label>Phone: </label>
                <input type="text" v-model="formData.phNo" required>
            </div>
            <div>
                <label>Email: </label>
                <input type="email" v-model="formData.emailAdd" required>
            </div>
            <div>
                <label>Favourite: </label>
                <input type="radio" name="favRadio" value="true" v-model="formData.isFavourite" required>Yes
                <input type="radio" name="favRadio" value="false" v-model="formData.isFavourite" required>No
            </div>
            <div>
                <button>Add friend</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'AddFriend',
        emits: ['add-contact'],
        data(){
            return{
                formData: {},
            }
        },
        methods:{
            submitFun(){
                this.$emit('add-contact', this.formData);
                this.formData = {};
            }
        },
    }
</script>

<style scoped>

</style>