<template>
  <section class="story-nav">
    <div class="logo flex" @click="$router.push('/')">
      <span class="svg-icon logo-icon" v-html="$svg('logo')"></span>
      <span
        class="svg-icon nav-btn logo-small"
        v-html="$svg('logoIcon')"
      ></span>
    </div>
    <div
      v-for="(btn, idx) in btns"
      class="nav-btn"
      :class="{ active: btn.name === $route.name }"
      @click="onChangeRoute(idx, btn.path)"
    >
      <span v-if="btn.svg" class="svg-icon" v-html="$svg(btn.svg)"></span>
      <img v-else class="user-img" :src="btn.imgUrl" alt="" />

      <span class="btn-title">{{ btn.title }}</span>
    </div>
    <div
    v-if="user"
      class="nav-btn"
      :class="{ active: 'Profile' === $route.name }"
      @click="onChangeRoute(idx, `/userProfile/${user._id}`)"
    >
      <img class="user-img" :src="user.imgUrl" alt="" />
      <span class="btn-title">Profile</span>
    
    </div>
    <!-- <div v-if="!user">
      <LoginSignUp />
    </div> -->
    <!-- <div  class="nav-btn" @click="$router.push('/')">
                    <span class="svg-icon" v-html="$svg('home')" ></span>
                    <span>Home</span>
                </div>
                <div  class="nav-btn">
                    <span class="svg-icon search-icon" v-html="$svg('search')" @click="$router.push('/')"></span>
                    <span>Search</span>
                </div>
                <div  class="nav-btn" @click="$router.push('/newStory')">
                    <span class="svg-icon" v-html="$svg('create')" ></span>
                    <span>Create</span>
                </div> -->
    <!-- <div  class="nav-btn">
                    <span class=""></span>
                    <span>Explore</span>
                </div>
                <div  class="nav-btn">
                    <span class=""></span>
                    <span>Messages</span>
                </div>
                <div  class="nav-btn">
                    <span class=""></span>
                    <span>Notifications</span>
                </div>
                <div  class="nav-btn">
                    <span class=""></span>
                    <span>Profile</span>
                </div>
                <div  class="nav-btn more">
                    <span class=""></span>
                    <span>More</span>
                </div> -->
  </section>
</template>

<script>
import LoginSignUp from '../Pages/LoginSignUp.vue';

export default {
    data() {
        return {
            btns: [
                {
                    id: 1,
                    isActive: true,
                    title: "Home",
                    name: "Home",
                    path: "/",
                    svg: "home",
                },
                // {
                //     id: 2,
                //     isActive: false,
                //     title: 'Search',
                //     name:'',
                //     path: '/',
                //     svg: 'search'
                // },
                {
                    id: 3,
                    isActive: false,
                    title: "Create",
                    name: "newStory",
                    path: "/newStory",
                    svg: "create",
                },
                // {
                //     id: 4,
                //     isActive: false,
                //     title: 'Profile',
                //     name:'Profile',
                //     path: `/userProfile/${this.$store.getters.getLoggedInUser._id}`,
                //     imgUrl:this.$store.getters.getLoggedInUser.imgUrl
                // },
                // {
                //     id: 4,
                //     title: 'login',
                //     name:'login',
                //     path: `/login`,
                //     svg: "heart",
                // },
            ],
        };
    },
    // path: `/userProfile/:${this.$store.getters.getLoggedInUser._id}`,
    methods: {
        onChangeRoute(idx, path) {
            // this.btns.forEach(btn => btn.isActive = false)
            // this.btns[idx].isActive = true
            // this.btns[idx].svg = `${this.btns[idx].svg}-fill`
            this.$router.push(path);
        },
    },
    watch: {},
    computed: {
        user() {
            // console.log(this.$store.getters.getLoggedInUser);
            return this.$store.getters.getLoggedInUser;
        },
    },
    components: { LoginSignUp }
};
</script>

<style lang="scss"></style>
