<template>
  <div class="listframe">
    <div class="itembox" v-for="(item, index) in limitedList" :key="index" :style="{ backgroundColor: colors[index % colors.length] }">
      <span class="oname"> {{ item.org_name }} </span>
      <button class="cbutton" @click="$emit('openInOganization', item)">
        Connect
      </button>
      <button class="dbutton">
        Delete
      </button>
    </div>
  </div>
</template>

<script>
import { createNamespacedHelpers } from 'vuex'
const { mapState } = createNamespacedHelpers('organizationInfo')

export default {
  name: 'OrganizationListItem',
  data() {
    return {
      colors: ["#AFA4C6a2", "#A4C6B5a2", "#A4BEC6a2", "#C6A4A4a2"],
      maxItems: 7,
    }
  },
  computed: {
    ...mapState({
      list: state => state.organizationInfos
    }),
    limitedList() {
      // 최대 개수로 제한된 아이템 리스트 반환
      return this.list.slice(0, this.maxItems);
    },
  }
}
</script>

<style scoped>
.listframe{
  display: block;
  margin-top: 2rem;
  margin-left: 3rem;
  margin-right: 3rem;
}
.itembox{
  margin-bottom: 0.7rem;
  background-color: #a4bec6a2;
  border-radius: 0.4rem;
  padding: 1rem 0;
}
.oname{
  padding-left: 2rem;
  width: 20rem;
  margin: 0;
}
.cbutton{
  font-size: 1rem;
  position: absolute;
  right: 11rem;
  color: white;
  background-color: #989898;
  padding-left: 1.8rem;
  padding-right: 1.8rem;
  border-radius: 0.2rem;
  border: none;
  box-shadow: 0 1px 1px 0.5px #0000002f;
  cursor:pointer;
}
.dbutton{
  font-size: 1rem;
  position: absolute;
  right: 4rem;
  color: white;
  background-color: #989898;
  padding-left: 1.8rem;
  padding-right: 1.8rem;
  border-radius: 0.2rem;
  border: none;
  box-shadow: 0 1px 1px 0.5px #0000002f;
  cursor:pointer;
}
</style>