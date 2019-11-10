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

    #profile {
        border-bottom: 1px dashed #a7a7a7;
        padding-bottom: 10px;
        margin-bottom: 10px;
    }

    #profile div:not(.clear-fix) {
        height: 190px;
        float: left;
        position: relative;
    }

    #profile .avatar {
        width: 35%;
        text-align: center;
    }

    #profile .avatar img {
        width: 180px;
    }

    #profile .info {
        width: 45%;
    }

    #profile #gpa {
        width: 20%;
    }

    #profile #gpa strong {
        position: absolute;
        width: 100%;
        height: 60px;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto auto;
        font-size: 60px;
        line-height: 60px;
        text-align: center;
    }

</style>