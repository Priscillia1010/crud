<template>
  <div class="container">
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Nama Sekolah</th>
          <th scope="col">Tahun</th>
          <th scope="col">Jurusan</th>
          <th scope="col">Jenjang</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(data, index) in datas" :key="index">
          <th scope="row">{{ data.id }}</th>
          <td>{{ data.nama_sekolah }}</td>
          <td>{{ data.tahun }}</td>
          <td>{{ data.jurusan }}</td>
          <td>{{ data.jenjang }}</td>
          <td>
            <Update
              class="mb-1"
              :id="data.id"
              :nama_sekolah="data.nama_sekolah"
              :tahun="data.tahun"
              :jurusan="data.jurusan"
              :jenjang="data.jenjang"
            ></Update>
            <Delete :id="data.id"></Delete>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from "axios";
import Update from "./ModalUpdate.vue";
import Delete from "./ModalDelete.vue";
export default {
  name: "TablePage",
  components: {
    Update,
    Delete,
  },
  data() {
    return {
      datas: [],
    };
  },
  created() {
    // let pendidikan = [
    //   {
    //     id: 1,
    //     nama_sekolah: "Ecole Children's House",
    //     tahun: 2007,
    //     jenjang: "TK",
    //     jurusan: "",
    //   },
    //   {
    //     id: 2,
    //     nama_sekolah: "Mahatma Gading School",
    //     tahun: 2011,
    //     jenjang: "SD",
    //     jurusan: "",
    //   },
    //   {
    //     id: 3,
    //     nama_sekolah: "Mahatma Gading School",
    //     tahun: 2017,
    //     jenjang: "SMP",
    //     jurusan: "",
    //   },
    //   {
    //     id: 4,
    //     nama_sekolah: "Mahatma Gading School",
    //     tahun: 2020,
    //     jenjang: "SMA",
    //     jurusan: "IPA",
    //   },
    //   {
    //     id: 5,
    //     nama_sekolah: "Binus University",
    //     tahun: 2023,
    //     jenjang: "Kuliah",
    //     jurusan: "Computer Science",
    //   },
    // ];
    axios.get("http://localhost:3000/pendidikan").then((pendidikan) => {
      this.datas = pendidikan.data;
    });
  },
};
</script>
<style></style>
