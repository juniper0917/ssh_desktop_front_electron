<template>
  <div class="topcat" @click="switch_top"> 
    <div class="category">
      Category
    </div>
    <img v-if="topbtn == true" src="@/assets/downSign.png">
    <img v-else src="@/assets/rightSign.png">
  </div>

  <div v-if="topbtn == true">
    <div v-for="(value, key) in this.getCategory" :key="key">
      <div class="level1" @click="select_l1(key)">
        <img v-if="l1btn == true && l1index == key" src="@/assets/downSign.png">
        <img v-else src="@/assets/rightSign.png">
        <span>
          {{ key }}
        </span>
      </div>

      <div v-if="l1btn == true && l1index == key">
        <div v-for="(server, indexl2) in value" :key="indexl2">
          <div class="level2" @click="select_l2(server)">
            <img src="@/assets/dotSign.png">
            <span>
              {{ server }}
            </span>
          </div>
        </div>
      </div>

    </div>
  </div>

</template>
  
<script>
import { createNamespacedHelpers } from 'vuex'
const { mapState, mapGetters, mapMutations } = createNamespacedHelpers('inOrganization')

export default {
  name: 'RightExpandingMenu',
  data() {
    return {
      topbtn: true,
      l1btn: false,
      l1index: "",
    }
  },
  computed: {
    ...mapState({
      projlist: state => state.projects,
      mode: state => state.mode
    }),
    ...mapGetters(['getCategory'])
  },
  methods: {
    ...mapMutations(['selectCatl1','selectCatl2']),
    switch_top(){
      this.topbtn = !this.topbtn
    },
    select_l1(index){
      this.selectCatl1(index)
      if(this.l1index != index){
        this.l1btn = true
      } else{
        this.l1btn = !this.l1btn
      }
      this.l1index = index
    },
    select_l2(server){
      this.selectCatl2(server)
    }
  },
}
</script>

<style scoped>
.topcat{
  cursor:pointer;
}
.category{
  display: inline;
  padding-left: 5%;
  height: 4.5rem;
  width: 70%;
  line-height: 400%;
  color: white;
}
.topcat img{
  margin-left: 8.6rem;
  width: 0.5rem;
  height: 0.5rem;
}
.level1{
  cursor:pointer;
  color: white;
  background-color: #383838;
}
.level1 img{
  margin-left: 1rem;
  width: 0.5rem;
  height: 0.5rem;
}
.level1 span{
  padding-left: 5%;
  line-height: 250%;
}
.level2{
  cursor:pointer;
  color: white;
  background-color: #2C2C2C;
}
.level2 img{
  margin-left: 2rem;
  margin-bottom: 0.2rem;
  width: 0.2rem;
  height: 0.2rem;
}
.level2 span{
  padding-left: 5%;
  line-height: 250%;
}
</style>