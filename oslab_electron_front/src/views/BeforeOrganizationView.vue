<template>
  <div class="container">

    <div class="leftsideframe">
      <AppInfo/>
      <NewOrganizationButton v-if="isLogin ==true" @openNewOrganModal="openNewOrganModal"/>
    </div>

    <div class="topbarframe">
      <TopBarButton />
    </div>

    <div class="contentframe">
      <template v-if="isLogin ==true && hasOrganization == true">
        <OrganizationListItem @openInOganization="openInOganization"/>
      </template>
      <div class="nocontent" v-else>
        Please Sign Up and Create New Organization !
      </div>
    </div>

  </div>
  <!-- <button @click="testIn()">
    화면 전환 버튼(개발용 추후 삭제)
  </button> -->

</template>

<script>
import AppInfo from '@/components/common/AppInfo.vue'
import NewOrganizationButton from '@/components/beforeorganization/NewOrganizationButton.vue'
import TopBarButton from '@/components/common/TopBarButton.vue'
import OrganizationListItem from '@/components/beforeorganization/OrganizationListItem.vue'
import { ipcRenderer } from 'electron'

import { createNamespacedHelpers } from 'vuex'
const { mapMutations, mapActions } = createNamespacedHelpers('inOrganization')
const { mapState } = createNamespacedHelpers('login')

export default {
  name: 'BeforeLoginView',
  data() {
    return {
      hasOrganization: true,
      organizationNames: [],
    }
  },
  computed: {
    ...mapState({
      isLogin: state => state.isLogin,
    }),
  },
  methods: {
    openNewOrganModal() {
      ipcRenderer.send('open-add-organ-modal')
    },
    openInOganization(org) {
      this.getProjects(org)
      this.setOrg(org)
    },
    ...mapMutations(['setOrg']),
    ...mapActions(['getProjects'])
  },
  components: {
    AppInfo,
    NewOrganizationButton,
    TopBarButton,
    OrganizationListItem
  }
}
</script>

<style scoped>
.container {
  position: relative;
  height: 100vh;
}

.leftsideframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 15rem;
  height: 100%;
  background-color: #444444;
}

.topbarframe {
  position: absolute;
  top: 0;
  left: 15rem;
  width: calc(100% - 15rem);
  height: 7rem;
  background-color: #373737;
}

.contentframe {
  position: absolute;
  top: 7rem;
  left: 15rem;
  width: calc(100% - 15rem);
  height: calc(100% - 7rem);
  background-color: #2B2B2B;
  color: white;
}
.nocontent{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
</style>