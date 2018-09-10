<template>
  <v-form v-model="valid">
    <v-text-field
      v-model="member"
      :rules="memberRules"
      label="กรอกข้อมูลค้นหา"
      required
    ></v-text-field>
     <v-btn color="primary" dark @click="Dosearch">ค้นหา
        <v-icon dark right>label</v-icon>
      </v-btn>
      <v-btn color="success" dark @click="Dosave">ล้างข้อมูล
        <v-icon dark right>label</v-icon>
      </v-btn>
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
  </div>
  </v-form>
</template>

<script>
export default {
  data () {
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
   
   this.getstudent()
  
      
  },
  methods: {
    async Dosearch() {
      console.log(this.member);
      let res = await this.$http.post("http://127.0.0.1/php_exams/search.php", {
        member: this.member
      })
      if (res.data.ok) {
        this.desserts = res.data.admin
      }
    },
    Dosave() {
      this.member = "";
    }
  }
  
}

</script>