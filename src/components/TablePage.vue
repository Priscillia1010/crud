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
        </tr>
      </thead>
      <tbody>
        <tr v-for="(data, index) in datas" :key="index">
          <th scope="row">{{ data.id }}</th>
          <td>{{ data.nama_sekolah }}</td>
          <td>{{ data.tahun }}</td>
          <td>{{ data.jurusan }}</td>
          <td>{{ data.jenjang }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "TablePage",
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
