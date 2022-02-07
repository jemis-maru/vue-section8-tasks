<template>
    <AddFriend @add-contact="addFriendFun" />
    <header>
      <h1>FriendList</h1>
    </header>
    <div v-for="fr in friendsArr" :key="fr.id">
        <FriendData :fr = 'fr' @toggle-par-fav="parToggleFav" @remove-contact="removeFun" />
    </div>
</template>

<script>
import FriendData from './components/FriendData.vue';
import AddFriend from './components/AddFriend.vue';

export default {
    name: 'App',
    components:{
        FriendData,
        AddFriend,
    },
    data(){
        return{
            friendsArr: [
                {
                    id: 'abc',
                    name: 'Abc Def',
                    phNo: '1234567890',
                    emailAdd: 'example@example.com',
                    isFavourite: true,
                },{
                    id: 'pqr',
                    name: 'Pqr Rst',
                    phNo: '1234567890',
                    emailAdd: 'example@example.com',
                    isFavourite: false,
                },
            ],
        }
    },
    methods: {
      parToggleFav(frId){
        let idOfFriend = this.friendsArr.find(friend => {
          return friend.id === frId;
        });
        idOfFriend.isFavourite = !idOfFriend.isFavourite;
      },
      addFriendFun(friendData){
        let newFrData = {
          id: friendData.name + Math.floor(Math.random()*100),
          name: friendData.name,
          phNo: friendData.phNo,
          emailAdd: friendData.emailAdd,
          isFavourite: friendData.isFavourite === 'true' ? true : false,
        };
        console.log(newFrData);
        this.friendsArr.push(newFrData);
      },
      removeFun(friendDelete){
        const index = this.friendsArr.indexOf(friendDelete);
        if (index != -1) {
          this.friendsArr.splice(index, 1);
        }
      },
    },
}
</script>

<style>
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

li, form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

input {
  border: none;
  border-bottom: 1px solid #000000;
}

button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

button:hover,
button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>