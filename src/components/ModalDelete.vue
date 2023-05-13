<template>
  <div>
    <div class="container">
      <b-button @click="$bvModal.show(id + '-delete')" variant="danger"
        >Delete Data</b-button
      >

      <b-modal :id="id + '-delete'">
        <template #modal-header="{ close }">
          <!-- Emulate built in modal header close button action -->
          <b-button size="sm" variant="outline-danger" @click="close()">
            X
          </b-button>
          <!-- <h5>Modal Header</h5> -->
        </template>

        <template>
          <!-- <div class="form-group">
            <label for="nama_sekolah">Name Sekolah</label>
            <input
              type="text"
              name="nama sekolah"
              class="form-control"
              placeholder="nama sekolah"
              v-model="nama_sekolah_data"
            />
          </div>

          <div class="form-group">
            <label for="tahun">Tahun</label>
            <input
              type="text"
              name="tahun"
              class="form-control"
              placeholder="tahun"
              v-model="tahun_data"
            />
          </div>

          <div class="form-group">
            <label for="jurusan">Jurusan</label>
            <input
              type="text"
              name="jurusan"
              class="form-control"
              placeholder="jurusan"
              v-model="jurusan_data"
            />
          </div>

          <div class="form-group">
            <label for="jenjang">Jenjang</label>
            <input
              type="text"
              name="jenjang"
              class="form-control"
              placeholder="jenjang"
              v-model="jenjang_data"
            />
          </div>
          {{ nama_sekolah }} - {{ tahun }} - {{ jurusan }} - {{ jenjang }} -->
          <h3>Are you sure want to delete this data ?</h3>
        </template>

        <template #modal-footer="{ cancel }">
          <!-- <b>Custom Footer</b> -->
          <!-- Emulate built in modal footer ok and cancel button actions -->
          <b-button size="sm" variant="success" @click.prevent="deleteData">
            OK
          </b-button>
          <b-button size="sm" variant="danger" @click="cancel()">
            Cancel
          </b-button>
          <!-- Button with custom close trigger value -->
          <!-- <b-button
            size="sm"
            variant="outline-secondary"
            @click="hide('forget')"
          >
            Forget it
          </b-button> -->
        </template>
      </b-modal>
      <br />
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "ModalDelete",
  props: ["id"],
  // data() {
  //   return {
  //     nama_sekolah_data: this.nama_sekolah,
  //     tahun_data: this.tahun,
  //     jurusan_data: this.jurusan,
  //     jenjang_data: this.jenjang,
  //   };
  // },
  methods: {
    deleteData() {
      axios
        .delete("http://localhost:3000/pendidikan/" + this.id)
        .then(() => {
          alert("data berhasil dihapus");
          window.location.reload(true);
        })
        .catch(() => {
          alert("data gagal dihapus");
          window.location.reload(true);
        });
    },
  },
};
</script>
<style scoped></style>
