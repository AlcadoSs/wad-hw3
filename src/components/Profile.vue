<template>

        <div id="profile" v-on="(user)">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{user.firstname}} {{user.lastname}}</li>
                    <li id="birthdate">{{user.birthdate}}</li>
                    <li id="faculty">{{user.faculty}}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{user.gpa}}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
</template>

<script>
    import User from "../models/User";

    export default {
        name: "Profile",
        data: () => {
            return {
                user:(
              new User("Siim", "Anderson", "12.04.1997", "Computer Science", 5.0))
            }
    },
    }
</script>

<style scoped>

</style>