<template>
  <v-navigation-drawer
    v-model="drawer"
    :mini-variant="miniVariant"
    :clipped="clipped"
    fixed
    app
  >
    <v-list>
      <v-list-item
        v-for="(item, i) in items"
        :key="i"
        :to="item.to"
        router
        exact
      >
        <v-list-item-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title v-text="item.title" />
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

// export default {
//   data () {
//     return {
//       clipped: false,
//       fixed: false,
//       items: [
//         {
//           icon: 'mdi-apps',
//           title: 'Welcome',
//           to: '/'
//         },
//         {
//           icon: 'mdi-chart-bubble',
//           title: 'Inspire',
//           to: '/inspire'
//         },
//         {
//           icon: 'mdi-home',
//           title: 'Register User',
//           to: '/addUser'
//         }
//       ],
//       miniVariant: false
//     }
//   }
// }
// </script>
