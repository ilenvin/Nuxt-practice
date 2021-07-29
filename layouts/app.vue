<template>
  <div>
    <AppDrawer />
    <AppToolbar />
    <AppRightDrawer />
    <AddUser />
    <AppFooter />
    <nuxt />
  </div>
</template>

<script>
import AddUser from '../components/AddUser'
import AppDrawer from '../components/AppDrawer'
import AppToolbar from '../components/AppToolbar'
import AppRightDrawer from '../components/AppRightDrawer'
import AppFooter from '../components/AppFooter'
export default {
  name: 'App',
  component: [
    AddUser,
    AppToolbar,
    AppRightDrawer,
    AppFooter,
    AppDrawer
  ]
}
</script>

<style scoped>

</style>
