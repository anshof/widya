<template>
  <div class="container">
    <div class="flex justify-start">
      <button
        class="border-0 bg-blue-800 text-white p-2 rounded-lg"
        @click="addStudents"
      >
        Tambah Staff
      </button>
    </div>
    <div
      class="border rounded-lg p-10 mt-4"
      v-for="(student, index) in students"
      v-bind:key="index"
    >
      <div class="flex justify-between">
        <p class="text-xl font-bold">Staff baru ( ke: {{ index + 1 }} )</p>
        <button
          class="border-0 bg-red-600 text-white px-2 rounded-lg"
          @click="deleteStudent(index)"
        >
          x
        </button>
      </div>
      <div class="mt-5">
        <input
          type="text"
          name="nama"
          placeholder="Nama"
          class="border rounded-lg block p-3 w-full mb-3"
          v-model.lazy="student.nama"
          required
        />
        <input
          type="text"
          name="alamat"
          class="w-full mb-3 border rounded-lg block p-3"
          placeholder="Alamat"
          v-model.lazy="student.alamat"
          required
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      students: [
        {
          nama: "",
          alamat: "",
        },
      ],
    };
  },
  methods: {
    addStudents() {
      this.students.push({
        nama: "",
        alamat: "",
      });
    },
    deleteStudent(index) {
      this.students.splice(index, 1);
    },
  },
};
</script>

<style scoped></style>
