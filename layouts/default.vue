<template>
  <v-app dark>
    <v-navigation-drawer :mini-variant="miniVariant" :clipped="clipped" fixed app>

      <v-list-item>
        <div class="px-2">
         <v-avatar>
          <img
            src="https://cdn.vuetifyjs.com/images/john.jpg"
            alt="John"
          >
        </v-avatar>
        </div>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            James Ulip
          </v-list-item-title>
          <v-list-item-subtitle>
            Programmer
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>
      <v-list>
        <v-list-item no-action sub-group v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>

        <v-list-group :value="true" prepend-icon="mdi-account-circle">
          <template v-slot:activator>
            <v-list-item-title>Users</v-list-item-title>
          </template>

          <v-list-group no-action sub-group>
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title>Admin</v-list-item-title>
              </v-list-item-content>
            </template>

            <v-list-item v-for="([link], i) in admins" :key="i" router :to="link.to">
              <v-list-item-title v-text="link.title"></v-list-item-title>
              <v-icon>{{link.icon}}</v-icon>
              <v-list-item-icon>
                <v-icon v-text="link.icon"></v-icon>
              </v-list-item-icon>
            </v-list-item>
          </v-list-group>


        </v-list-group>
      </v-list>

      <template v-slot:append>
        <v-list>
          <v-list-item @click="$auth.logout(/* .... */)">
            <v-list-item-action>
              <v-icon>mdi-logout</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="`Logout`" />
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </template>

    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="miniVariant = !miniVariant" />
      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item>
            <v-list-item-title>Admin Page</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-toolbar-title v-text="title" @click="logoutUser()"/>
      <v-spacer />

    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    middleware: ['auth'],
    data() {
      return {
        clipped: true,
        drawer: false,
        fixed: false,
        admins: [
          [{
              title: 'Settings',
              to: '/settings'
            },
            {
              title: 'Permission',
              to: '/'
            },
            {
              title: 'Roles',
              to: '/'
            },
          ],
        ],
        items: [{
            icon: 'mdi-apps',
            title: 'Welcome',
            to: '/'
          },
          {
            icon: 'mdi-clipboard-edit-outline',
            title: 'Inventory',
            to: '/inspire'
          },
          {
            icon: 'mdi-format-list-checks',
            title: 'Categories',
            to: '/categories'
          },

        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Inventory'
      }
    },
    methods:{
      async logoutUser(){
        await this.$auth.logout()
        this.$router.push('/login')
      }
    }
  }

</script>
