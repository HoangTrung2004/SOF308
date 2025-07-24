<template>  
<h1 class="text-danger mt-5">Bài 4</h1>
    <div class="row">
        <form @submit.prevent="submitForm" class="col-sm-4 border rounded p-3 bg-light">
            <h3>Thêm học sinh</h3>
            <div class="mb-3">
                <label for="name">Họ và tên:</label>
                <input type="text" v-model="student.name" id="name" class="form-control" required >
            </div>

            <div class="mb-3">
                <label for="score">Điểm:</label>
                <input type="number" v-model="student.score" id="score" class="form-control" required >
            </div>
            <div class="mb-3">
                <label for="dob">Ngày sinh:</label>
                <input type="date" v-model="student.dob" id="dob" class="form-control" required>
            </div>

            <button type="submit" class="btn btn-success">{{ isEditing ? 'Cập nhật' : 'Thêm' }}</button>
        </form>

        <!-- DANH SÁCH HỌC SINH -->
         <div class="col-sm-8">
            <h3>Danh sách học sinh</h3>
            <table class="table table-hover ">
                <thead>
                    <tr>
                        <th>Họ và tên</th>
                        <th>Điểm</th>
                        <th>Ngày sinh</th>
                        <th></th>
                        <th></th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(stu, index) in students" :key="index">
                        <td>{{ stu.name }}</td>
                        <td>{{ stu.score }}</td>
                        <td>{{ stu.dob }}</td>
                        <td class="btn btn-warning" @click="editStudent(index)">Sửa</td>
                        <td class="btn btn-danger" @click="deleteStudent(index)">Xóa</td>
                    </tr>
                </tbody>
            </table>
         </div>
    </div>
</template>

<script setup>
    import {ref} from 'vue';

    const students = ref([
        {name: 'Nguyễn Chí Hùng', score: 8, dob: '2006-01-01'},
        {name: 'Phạm Thị Loan ', score: 9, dob: '2006-01-01'}
    ]);

    const student = ref({
        name: '',
        score: null,
        dob: ''
    });

    const isEditing = ref(false); // false: đang thêm mới, true: đang sửa
    let isEditingIndex = ref(null);
    
    // HÀM XỬ LÝ
function submitForm(){
    if(isEditing.value){
        students.value[isEditingIndex.value] = {...students.value}
        isEditing.value = false;
        isEditingIndex.value = null;
    }else{
        students.value.push({...student.value})
    }
    resetForm();
}
    //SỬA
function editStudent(index){
    student.value = {...students.value[index]};
    isEditing.value = true;
    isEditingIndex.value = index;
}
    //XÓA
function deleteStudent (index){
    students.value.slice(index, 1); // xóa 1 phàn tử ở vị trí index
    resetForm();
}
    // RESET
function resetForm (){
    student.value = {
        name: '',
        score: '',
        dob: ''
    };
    isEditing.value = false;
    isEditingIndex = null;
}

 </script>