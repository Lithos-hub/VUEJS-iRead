<template>
  <div>
    <v-app-bar color="white" dark app>
      <v-app-bar-nav-icon
        @click="drawer = true"
        color="black"
        class="my-auto"
      ></v-app-bar-nav-icon>

    <router-link to="/main">

     <v-toolbar-title class="brand-title"> 
        <span id="i">i</span>
        <span id="r">R</span>
        <span id="e">e</span>
        <span id="a">a</span>
        <span id="d">d</span>
      </v-toolbar-title>

    </router-link>

      <v-spacer></v-spacer>
      <router-link to="/access" style="text-decoration: none" class="ma-auto mx-2">
        <v-btn color="success" outlined class="my-auto">Login / Register<v-icon>mdi-account</v-icon></v-btn>
      </router-link>
      <v-btn color="error" class="my-auto">Sign out<v-icon>mdi-account-cancel</v-icon></v-btn>
      <router-link to="/about" style="text-decoration: none" class="ma-auto mx-2">
        <v-btn color="info" class="my-auto">About</v-btn>
      </router-link>
      <a
        href="https://github.com/Lithos-hub/VUEJS-iRead"
        style="text-decoration: none"
        class="ma-auto"
      >
        <v-btn color="secondary" class="my-auto"
          ><v-icon color="white">mdi-github</v-icon></v-btn
        >
      </a>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" temporary app>
      <router-link to="/changelog" style="text-decoration: none;">
        <v-btn color="secondary" tile class="cyan--text" block>Changelog</v-btn>
      </router-link>
      <v-list class="nav-list" dense>
        <v-list-item-title class="text-h6 ml-5 text--disabled"
          >Account</v-list-item-title
        >
        <v-list-item-group v-model="group">
          <v-list-item v-for="(item, i) in account" :key="'A' + i">
            <router-link :to="item.to" style="text-decoration: none" class="router-link">
              <v-list-item-icon>
                <v-icon class="nav-icon">{{ item.icon }}</v-icon>
                <v-list-item-title class="nav-text">{{ item.text }}</v-list-item-title>
              </v-list-item-icon>
            </router-link>
          </v-list-item>
        
        <v-list-item-title class="text-h6 ml-5 text--disabled"
          >Discover</v-list-item-title
        >
    
          <v-list-item v-for="(item, i) in discover" :key="'B' + i">
            <router-link :to="item.to" style="text-decoration: none" class="router-link">
              <v-list-item-icon>
                <v-icon class="nav-icon">{{ item.icon }}</v-icon>
                <v-list-item-title class="nav-text">{{ item.text }}</v-list-item-title>
              </v-list-item-icon>
            </router-link>
          </v-list-item>
      
        <hr class="menu-divider" />
        <v-list-item-title class="text-h6 ml-5 text--disabled"
          >My collections</v-list-item-title
        >
  
          <v-list-item v-for="(item, i) in collections" :key="'C' + i">
            <router-link :to="item.to" style="text-decoration: none" class="router-link">
              <v-list-item-icon>
                <v-icon class="nav-icon">{{ item.icon }}</v-icon>
                <v-list-item-title class="nav-text">{{ item.text }}</v-list-item-title>
              </v-list-item-icon>
            </router-link>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  data: () => ({
    version: 0,
    subversion: 1,
    drawer: false,
    group: null,
    account: [
      {to: "/account", icon: "mdi-account", text: "My account"},
    ],
    collections: [
      { to: "/mybooks", icon: "mdi-book", text: "My Books" },
      { to: "/wishlist", icon: "mdi-format-list-bulleted-square", text: "Wish List" },
      { to: "/alreadyread", icon: "mdi-check", text: "Already Read" },
    ],
    discover: [
      { to: "/main", icon: "mdi-home", text: "Main" },
      { to: "/genres", icon: "mdi-table", text: "By Genres" },
      { to: "/bestsellers", icon: "mdi-star", text: "Best Sellers" },
    ],
  }),
};
</script>

<style lang="scss">
@import "src/scss/variables";

#navbar {
  border-bottom: 1px solid gray;
  padding: 0;
}

#i {
    position: relative;
    color: $googleBlue;
  }
  #r {
    position: relative;
    color: $googleRed;
  }
  #e {
    position: relative;
    color: $googleYellow;
  }
  #a {
    position: relative;
    color: $googleBlue;
  }
  #d {
    position: relative;
    color: $googleGreen;
  }


.brand-title {
  font-family: $style5;
  font-weight: bold;
}

#and {
  font-family: $style5;
  font-weight: bold;
  color: #505050;
}

.api {
  color: $googleBlue;
  display: flex;
  margin-left: 10px;
  font-family: $style5;
}

.nav-list {
  margin-top: 50px;
}

.nav-link {
  padding-top: 20px;
  padding-bottom: 20px;
  margin: 0;
  margin-left: 20px;
}

.router-link {
  width: 100%;
}

.nav-link:hover {
  background-color: $secondary;
  color: white !important;
}

.search-btn {
  border: 2px solid $secondary;

  &:hover {
    background: $primary;
    color: white;
  }
}

.search-input {
  transition: 1s;

  &:hover {
    padding-right: 60px;
    padding-left: 10px;
    border-radius: 0px 0px 0px 5px;
    box-shadow: 0px 0px 5px;
  }
  &:focus {
    outline: none;
  }
}

#version-info {
  font-size: 14px;
}

.nav-icon {
  position: absolute;
  left: 5px;
  font-size: 20px !important;
}

.nav-text {
  position: absolute;
  margin: 0 auto;
  right: 25px;
  font-size: 14px !important;
}

.menu-divider {
  background: $googleBlue;
  border: 1px solid $googleBlue;
}
</style>
