<template>
  <div class="home">

    <nav>
      <v-app-bar bdense app color="black">
<!--        <v-app-bar-nav-icon class="grey&#45;&#45;text" @click="drawer=!drawer"></v-app-bar-nav-icon>-->
        <v-toolbar-title class="text-uppercase grey--text">
          <span class="font-weight-light">Three</span>
          <span>js</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
          <v-btn small text color="grey">
              <span >Sign Out</span>
              <v-icon right>exit_to_app</v-icon>
          </v-btn>
      </v-app-bar>
    </nav>
    <v-navigation-drawer permanent expand-on-hover app v-model="drawer" color="grey darken-4">
      <v-list>
        <v-list-item>
          <v-list-item-avatar>
            <v-icon class="white--text">dashboard</v-icon>
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="white--text">Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-card
              class="mx-auto"
              width="300"
      >
        <v-list>
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>

            <v-list-item-title>Home</v-list-item-title>
          </v-list-item>

          <v-list-group
                  :value="true"
                  prepend-icon="mdi-account-circle"
          >
            <template v-slot:activator>
              <v-list-item-title>Users</v-list-item-title>
            </template>

            <v-list-group
                    :value="true"
                    no-action
                    sub-group
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>Admin</v-list-item-title>
                </v-list-item-content>
              </template>

              <v-list-item
                      v-for="([title, icon], i) in admins"
                      :key="i"
                      link
              >
                <v-list-item-title v-text="title"></v-list-item-title>

                <v-list-item-icon>
                  <v-icon v-text="icon"></v-icon>
                </v-list-item-icon>
              </v-list-item>
            </v-list-group>

            <v-list-group
                    no-action
                    sub-group
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>Actions</v-list-item-title>
                </v-list-item-content>
              </template>

              <v-list-item
                      v-for="([title, icon], i) in cruds"
                      :key="i"
                      link
              >
                <v-list-item-title v-text="title"></v-list-item-title>

                <v-list-item-icon>
                  <v-icon v-text="icon"></v-icon>
                </v-list-item-icon>
              </v-list-item>
            </v-list-group>
          </v-list-group>
        </v-list>
      </v-card>
    </v-navigation-drawer>

    <div id="threeJs">
        <Threejs></Threejs>
    </div>
  </div>
</template>

<script>
    import Threejs from "../components/Threejs";

export default {
  name: 'Home',
  components: {
    Threejs
  },
  data(){
    return{
      drawer:true,
      admins: [
        ['Management', 'mdi-account-multiple-outline'],
        ['Settings', 'mdi-cog-outline'],
      ],
      cruds: [
        ['Create', 'mdi-plus-outline'],
        ['Read', 'mdi-file-outline'],
        ['Update', 'mdi-update'],
        ['Delete', 'mdi-delete'],
      ],
    }
  }
}
</script>
