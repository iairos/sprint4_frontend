<script>
import StoryNav from '@/cmps/StoryNav.vue'
import LoginSignUp from '@/Pages/LoginSignUp.vue';

export default {

    async created(){
        // const user = await this.$store.dispatch({ type: 'loadUser' })
        this.$store.dispatch({ type: 'loadStories' })
        this.$router.push('/login')
        // userService.login({username:'jeniferbabiston', password:'abc'})        
    },
    components: {
        StoryNav,
        LoginSignUp
        
        
    },
    methods:{
       

    },
}
</script>

<template>
    <section class="main-layout" >
        <!-- show storyNav v-if="userLogged" -->
        <StoryNav/> 
        <RouterView />
    </section>
</template>

<style scoped lang="scss">
.main-layout{
    display: flex;
    height: 100vh;
//   grid-template-columns: 1fr 4fr 2fr;
//   margin: 0 auto;
}
</style>