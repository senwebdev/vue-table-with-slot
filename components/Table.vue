<template>
  <table class="table">
    <thead>
      <slot name="columns">
        <th v-for="column in columns">{{ column }}</th>
      </slot>
    </thead>
    <tbody>
      <template v-for="item in data">
        <tr @click="item.expanded = !item.expanded;">
          <slot :row="item">
            <td
              v-for="(column, index) in columns"
              v-if="hasValue(item, column)"
            >
              <i
                v-if="index === 0"
                class="fa fa-chevron-right arrow"
                :class="{ rotate: item.expanded }"
              ></i>
              {{ itemValue(item, column) }}
            </td>
          </slot>
        </tr>
        <tr v-if="item.expanded">
          <td colspan="2"><p>Expanded</p></td>
        </tr>
      </template>
    </tbody>
  </table>
</template>
<script>
export default {
  name: "l-table",
  props: {
    columns: Array,
    data: Array
  },
  methods: {
    hasValue(item, column) {
      return item[column.toLowerCase()] !== "undefined";
    },
    itemValue(item, column) {
      return item[column.toLowerCase()];
    }
  }
};
</script>
<style lang="scss">
$primary-color: #66615b;
$gray-color: #f2f2f2;

.table {
  width: 100%;
  box-shadow: 0 6px 10px -4px rgba(0, 0, 0, 0.15);
}

.arrow {
  transition: all 0.2s;
  &.rotate {
    transform: rotateY(90deg);
  }
}
td,
th {
  padding: 10px;
}

tr:nth-child(even) {
  background-color: $gray-color;
}

tr:hover {
  background-color: #ddd;
  transition: background-color 0.2s ease-in;
  cursor: pointer;
}

th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: $primary-color;
  color: white;
}
</style>
