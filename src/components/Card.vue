<script setup>
    import {defineProps, ref} from "vue";
    import {useRouter} from "vue-router";
    
    const router = useRouter();
    const {quiz} = defineProps(['quiz']);
  
   // console.log(quiz);


    const navigateToQuiz = (id) => {
    quiz.forEach(element => {
     // console.log('elementID =>', element.id);
      if(id === element.id) {
        router.push(`/card/${element.id}`);
      }
    });
     
    }

</script>

<template>
 <div class="card" 
        v-for="q in quiz" :key="q.id" @click="navigateToQuiz(q.id)">
        <img :src="q.img" alt="Quiz image">
        <div class="card-text">
          <h2>{{q.name}}</h2>
          <p>{{ q.questions.length }} questions</p>
        </div>
      </div>
</template>

<style scoped>

.card {
    width: 310px;
    overflow: hidden;
    border-radius: 8px;
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
    background-color: white;
    -webkit-box-shadow: 0px 0px 17px -3px rgba(0,0,0,0.91); 
    box-shadow: 0px 0px 17px -3px rgba(0,0,0,0.91);
  }

  .card img {
    width: 100%;
    height: 190px;
    margin: 0;
  }

  .card .card-text {
    padding: 8px;
    color:black;
  }
</style>