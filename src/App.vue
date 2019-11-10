<template>
    <main id="app">
        <Header/>
        <Footer/>

        <section id="container">
            <section id="main">
                <div class="content">
                    <div id="profile-container" class="tab" :class="{ active: isActive('profile') }">
                        <Profile/>
                    </div>
                    <div id="courses-container" class="tab" :class="{ active: isActive('courses') }">
                        <Courses/>
                    </div>
                </div>
                <div class="controls">
                    <button id="profile-button" class="pill"    @click="setActive('profile')" :class="{ active: isActive('profile') }">Profile</button>
                    <button id="courses-button" class="pill" @click="setActive('courses')" :class="{ active: isActive('courses') }">Courses</button>
                </div>
            </section>
        </section>
    </main>
</template>

<script>

    import Header from './components/Header.vue'
    import Footer from './components/Footer.vue'
    import Profile from './components/Profile.vue'
    import Courses from './components/Courses.vue'

    export default {
        name: 'app',
        components: {
            Header,
            Footer,
            Profile,
            Courses
        },

        data() {
            return { activeItem: 'profile' }
        },
        methods: {
            isActive: function (menuItem) {
                return this.activeItem === menuItem
            },
            setActive: function (menuItem) {
                this.activeItem = menuItem
            }
        }
    }


</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    .clear-fix {
        clear: both;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }


    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }

    .content .tab {
        display: none;
    }

    .content .tab.active {
        display: block;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }

</style>
