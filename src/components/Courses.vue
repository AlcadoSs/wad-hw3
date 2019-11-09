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
            <button id="add-course-button" class="blue-button">+</button>
            <span id="add-course">
                <input class="input" type="text" placeholder="Course title" id="title">
                <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
                <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
                <button class="green-button" id="save-course">Save</button>
                <button class="grey-button" id="cancel-course">Cancel</button>
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
                courses: [
                    new Course("Operation systems", 1, 98),
                    new Course("Software Engineering", 1, 55),
                    new Course("Algorithms and Data Structures", 1, 68),
                    new Course("Introduction to Data Science", 1, 76)
                ]
            }
        },
    }
</script>

<style scoped>

</style>