<template>
	<tr v-bind:class="'present=' + student.present">
		<td> {{ student.name }} </td>
		<td> {{ student.starID }} </td>
		<td> <input type="checkbox" v-model="student.present" v-on:change="checked(student)"></td>
		<td v-show="edit"> 
			<button id="delete-button" v-on:click="deleteStudent(student)">x</button>
		</td>
	</tr>
</template>

<script>
export default {
	name: "StudentRow",
	props: {
		student: Object,
		edit: Boolean
	},
	methods: {
		checked(student){
			this.$emit("student-present",student)
		},
		deleteStudent(student){
			if(confirm(`Delete ${student.name}?`)){
				console.log("Row")
				this.$emit("delete-student", student)
			}
		}
	}
}
</script>

<style>
	.present-true{
		color: gray;
		font-style: italic;
	}
	.present-false{
		font-weight: bold;
	}
	button{
		border-radius: 50%;
		background-color: red;
		color: white;
	}
</style>
