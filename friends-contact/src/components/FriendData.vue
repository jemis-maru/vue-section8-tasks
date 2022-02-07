<template>
    <ul>
        <li>
            <h2>{{ fr.name }} {{favouriteText}}</h2>
            <div>
                <button @click="toggleFavourite">{{ btnFavouriteFun }}</button>
            </div>
            <br>
            <div>
                <button @click="toggleDetails">{{ btnTextFun }}</button>
            </div>
            <br>
            <div>
                <button @click="removeContact">Delete contact</button>
            </div>
            <ul v-show="detailsToggle">
                <li><strong>Phone: </strong>{{ fr.phNo }}</li>
                <li><strong>Email: </strong>{{ fr.emailAdd }}</li>
            </ul>
        </li>
    </ul>
</template>

<script>
export default {
    name: 'FriendData',
    props:{
        fr: {
            type: Object,
        },
    },
    emits: ['toggle-par-fav', 'remove-contact'],
    data(){
        return{
            detailsToggle: false,
            // isFrFavourite: this.fr.isFavourite,
        }
    },
    methods:{
        toggleDetails(){
            this.detailsToggle = !this.detailsToggle;
        },
        toggleFavourite(){
            // this.isFrFavourite = !this.isFrFavourite;
            this.$emit('toggle-par-fav', this.fr.id);
        },
        removeContact(){
            this.$emit('remove-contact', this.fr);
        },
    },
    computed:{
        btnTextFun(){
            if(this.detailsToggle){
                return 'Hide details';
            }
            else{
                return 'Show details';
            }
        },
        btnFavouriteFun(){
            if(this.fr.isFavourite){
                return 'Remove from favourite';
            }
            else{
                return 'Add to favourite';
            }
        },
        favouriteText(){
            if(this.fr.isFavourite){
                return '- Favourite';
            }
            else{
                return '';
            }
        }
    },
}
</script>