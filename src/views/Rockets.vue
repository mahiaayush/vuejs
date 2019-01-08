<template lang="html">
  <section>
    <nav-bar></nav-bar>
    <new-rocket-form :addRocket="addRocket" ></new-rocket-form>
    <rocket-list :rockets="rockets" :removeRocket="removeRocket"></rocket-list>
  </section>
</template>

<script>
import NavBar from '@/components/NavBar';
import NewRocketForm from '@/components/NewRocketForm';
import RocketList from "@/components/RocketList"
import API from '@/lib/API'
export default {
  components: {
    NewRocketForm,
    NavBar,
    RocketList,

  },
  data :()=>({
    rockets:[],
  }),
  async mounted() {
  this.rockets = await API.getRockets();
  //console.log(rockets);
},methods: {
  addRocket(rocket) {
    this.rockets.push(rocket);
  },
  removeRocket(rocket){
    debugger
    const index=this.rockets.indexOf(rocket);
    this.rockets.slice(index,1);
  }
}
};
</script>
