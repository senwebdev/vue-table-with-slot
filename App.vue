<template>
  <div id="app">
    <CustomTable :data="tableData" :columns="tableColumns"> </CustomTable>

    <div class="table-separator"></div>

    <CustomTable :data="tableData">
      <template slot="columns">
        <th>Title</th>
        <th><i class="fa fa-images"></i> Image</th>
        <th class="actions-row">
          <i class="fab fa-vuejs vue-icon"></i> Actions
        </th>
      </template>

      <template slot-scope="{ row }">
        <td class="bold-row">{{ row.title }}</td>
        <td class="img-row"><img :src="row.img" /></td>
        <td class="actions-row">
          <button @click.native="handleAction('Edit');">
            <i class="fa fa-edit"></i>
          </button>
          <button @click.native="handleAction('Delete');" type="danger">
            <i class="fa fa-trash"></i>
          </button>
        </td>
      </template>
    </CustomTable>
  </div>
</template>

<script>
import CustomTable from "./components/Table.vue";
import Button from "./components/Button.vue";
export default {
  name: "app",
  components: {
    CustomTable,
    Button
  },
  data() {
    return {
      tableData: [
        {
          text: "First item",
          title: "First",
          icon: "fa fa-user",
          img: "http://placehold.it/150/24f355",
          expanded: true
        },
        {
          text: "Second item",
          title: "Second",
          icon: "fa fa-copy",
          img: "http://placehold.it/150/f66b97"
        },
        {
          text: "Third item",
          title: "Third",
          icon: "fa fa-cut",
          img: "http://placehold.it/150/56a8c2"
        }
      ],
      tableColumns: ["text", "title"]
    };
  },
  methods: {
    handleAction(type) {
      alert(`You clicked ${type}`);
    }
  }
};
</script>

<style lang="scss">
$primary-color: #66615b;
$danger-color: #eb5e28;
$success-color: #41b883;

.table-separator {
  margin-top: 50px;
}
.bold-row {
  font-weight: 700;
  color: $primary-color;
}
.img-row img {
  width: 50px;
  height: 50px;
}

.actions-row {
  display: flex;
  justify-content: center;
  .btn {
    margin-right: 10px;
  }
  .vue-icon {
    color: $success-color;
    font-size: 20px;
  }
}
</style>
