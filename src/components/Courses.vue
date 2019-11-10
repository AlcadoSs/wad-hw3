<template>
    <div>
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
            </thead>
            <tbody v-for="(course, index) in courses" :key="index">
            <tr>
                <td>{{index+1}}</td>
                <td>{{course.title}}</td>
                <td>{{course.semester}}</td>
                <td>{{course.grade}}</td>
            </tr>
            </tbody>
        </table>
        <br>
        <br>
        <div>
            <button id="add-course-button" class="blue-button" v-on:click="addCourse = !addCourse">+</button>
            <span id="add-course" v-show="addCourse">
                <input class="input" type="text" placeholder="Course title" id="title">
                <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
                <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
                <button class="green-button" id="save-course" @click="save()">Save</button>
                <button class="grey-button" id="cancel-course" @click="cancel()">Cancel</button>
             </span>
        </div>
    </div>
</template>

<script>
    import Course from "../models/Course";

    export default {
        name: "Courses",
        data: () => {
            return {
                addCourse:false,
                courses: [
                    new Course("Operation systems", 1, 98),
                    new Course("Software Engineering", 1, 55),
                    new Course("Algorithms and Data Structures", 1, 68),
                    new Course("Introduction to Data Science", 1, 76)
                ],

            }
        },

    }
</script>

<style scoped>

    .blue-button {
        background-color: #2196F3;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .green-button {
        background-color: #69f378;
        color: #ffffff;
        border: none;
        padding: 10px 10px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
    }

</style>