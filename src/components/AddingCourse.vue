<template>
    <v-container>
        <v-row>
            <h1>Add Course</h1>
        </v-row>
        <v-row>
            <v-col>
                Course Name:
            </v-col>
            <v-col>
                <v-text-field
                v-model="courseObject.course_name"
                ></v-text-field>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                Course Number:
            </v-col>
            <v-col>
                <v-text-field
                v-model="courseObject.course_num"
                ></v-text-field>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                Description:
            </v-col>
            <v-col>
                <v-text-field
                v-model="courseObject.course_desc"
                ></v-text-field>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                Course Hours:
            </v-col>
            <v-col>
                <v-text-field
                v-model="courseObject.course_hours"
                ></v-text-field>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                Course Department:
            </v-col>
            <v-col>
                <v-text-field
                v-model="courseObject.course_dept"
                ></v-text-field>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                Class Level:
            </v-col>
            <v-col>
                <v-text-field
                v-model="courseObject.course_level"
                ></v-text-field>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-btn v-on:click.native = "addClass" color="primary">Add</v-btn>
            </v-col>
            <v-col>
                <v-btn color="primary" :to="{ name: 'Home'}">Back</v-btn>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import CourseService from "@/services/CourseService.js";
import router from "@/router/index.js";
export default {
    name: "AddCourse",
    props: [],
    methods:{
        addClass(){
            CourseService.postCourse(this.courseObject)
            .then(response => {
                router.push({ name: 'Home'});
                console.log(response.data);
            })
            .catch(error => {
                console.log("There was an error" + error.response)
            });
        }
    },
    data: () => ({
        courseObject: {
            course_name: "",
            course_dept: "",
            course_num: "",
            course_level: "",
            course_hours: "",
            course_desc: ""
        }
    }),
}
</script>