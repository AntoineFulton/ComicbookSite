<template>
  <div class="home"> 
    <h1>Welcome to BT Comics</h1>  
    <div class="collection-container">
      <collection-card v-for="collection in collections" v-bind:key="collection.name" :collection="collection"></collection-card>
    </div>
  </div>
</template>

<script>
import CollectionCard from "../components/CollectionCard.vue";
import CollectionService from '../services/CollectionService.js';

export default {
  name: "home",
  components: {
    CollectionCard
  },
  data()
  {
    return {
      collections:[]
    }
  },
  created()
  {
    CollectionService.getLimitedCollections(4).then(response => 
    {
      this.collections = response.data;
    });
  } 
}
</script>

<style>
  /* div.home {
    background-image: url("../../assets/Images/blue backgd.jpg");
    background-size: 100%;
    
    background-repeat: no-repeat;    
  } */

 .home {
   color: white;
   text-shadow: 2px 2px black;
   text-align: center;
   margin:0;

 }
 h2
 {
   max-width: 100%;
   white-space: nowrap;
 }

 h1{
   margin-top:10%;
   font-size: 70px;
 }

 .collection-container
 {
  width: 100vw;
   display: flex;
   flex-direction: row;
   justify-content: space-around;
   flex-wrap: wrap;
   margin:0;
 }

 @media only screen and (orientation:portrait) {

   h1
   {
     margin-top:10vh
   }

   #title
   {
     max-width:100%;
     
   }

   .card
  {
    min-width:100%;
    min-height: 100%;
    margin:0px;
  }

   .collection-container
   {
     max-width:95vw;
     margin-top:-20vh;
     flex-wrap: wrap;
   }

 }
 
</style>
