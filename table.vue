<template>
<div>
  <v-data-table
    :headers="headers"
    :items="desserts"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.m_id }}</td>
      <td class="text-xs-lelt">{{ props.item.m_name }}</td>
      <td class="text-xs-lelt">{{ props.item.m_username }}</td>
      <td class="text-xs-lelt">{{ props.item.m_password }}</td>
      
      
    </template>
    
    <template slot="pageText" slot-scope="props">
      Lignes {{ props.pageStart }} - {{ props.pageStop }} de {{ props.itemsLength }}
    
    </template>
  </v-data-table>
   <div>
    <v-btn color="success">เพิ่ม</v-btn>
    <v-btn color="warning">แก้ไข</v-btn>
    <v-btn color="error">ลบ</v-btn>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "ID",
          align: "left",
          sortable: false,
          value: "name"
        },
       { text: "รหัส", value: "รหัส" },
        { text: "ชื่อ-สกุล", value: "ชื่อ-สกุล" },
        { text: "วันที่ยืมหนังสือ", value: "วันที่ยืมหนังสือ" },
        { text: "จำนวน/เล่ม ", value: "จำนวน/เล่ม" }
      ],
      desserts: []
    };
  },
  async created() {
    this.getstudent();
  },
  methods: {
    async getstudent() {
      let res = await this.$http.get(
        "http://127.0.0.1/php_exams/list-student.php"
      );
      this.desserts = res.data.student;
    }
  }
};
</script>