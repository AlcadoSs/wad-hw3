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
                <strong>{{gpa()}}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
</template>

<script>
    import User from "../models/User";
    import courses from "../components/Courses";

    export default {
        name: "Profile",
        data: () => {
            return {
                user:(
              new User("Siim", "Anderson", "12.04.1997", "Computer Science", 5.0))
            }
    },

        methods: {

            gpa: function () {

                let gpa = 0;
                for (let i = 0; i < courses.data().courses.length; i++) {
                    let grade = courses.data().courses[i].grade;
                    if (grade >= 90) {
                        gpa += 4;
                    } else if (grade >= 80) {
                        gpa += 3;
                    } else if (grade >= 70) {
                        gpa += 2;
                    } else if (grade >= 60) {
                        gpa += 1;
                    } else if (grade >= 50) {
                        gpa += 0.5;
                    } else {
                        gpa += 0;
                    }
                }
                gpa = gpa / courses.data().courses.length;

                return gpa;
            },
        }
    }
</script>

<style scoped>

</style>