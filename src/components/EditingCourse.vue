<template>
    <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
            <v-col cols="7">
                <v-row>
                    <v-col>
                        <h1>Edit Course</h1>
                    </v-col>
                </v-row>
                <v-divider></v-divider>
                <v-row>
                    <v-col>
                        <p>Course name:</p>
                    </v-col>
                    <v-col>
                        <v-text-field
                        v-model = "courseObject.course_name"
                        ></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <p>Course Number:</p>
                    </v-col>
                    <v-col>
                        <v-text-field
                        v-model="courseObject.course_num"
                        ></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <p>Description:</p>
                    </v-col>
                    <v-col>
                        <v-text-field
                        v-model = "courseObject.course_desc"
                        ></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <p>Course Hours:</p>
                    </v-col>
                    <v-col>
                        <v-text-field
                        v-model = "courseObject.course_hours"
                        ></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <p>Course Department:</p>
                    </v-col>
                    <v-col>
                        <v-text-field
                        v-model = "courseObject.course_dept"
                        ></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <p>Class Level:</p>
                    </v-col>
                    <v-col>
                        <v-text-field
                        v-model = "courseObject.course_level"
                        ></v-text-field>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col align = "center">
                        <v-btn v-on:click.native = "saveClass" color="primary">Save</v-btn>
                    </v-col>
                    <v-col align = "center">
                        <v-btn color="primary" :to="{ name: this.returnTo, params: { courseIndex: courseObject.course_id }}">Cancel</v-btn>
                    </v-col>
                </v-row>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import CourseService from "@/services/CourseService.js";
import router from "@/router/index.js";
export default {
    name: "EditCourse",
    props: ['courseObject', 'returnTo'],
    methods:{
        saveClass(){
            console.log("button clicked");
            console.log(this.courseObject.course_id);
            console.log(this.courseObject);
            CourseService.putCourse(this.courseObject.course_id, this.courseObject)
            .then( () => {
                router.push({ name: this.returnTo, params: { courseIndex: this.courseObject.course_id }});
            })
            .catch(error => {
                console.log("Save class error: " + error.response);
            });
        }
    },
    data: () => ({
        
    }),
}
</script>
