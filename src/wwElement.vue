<template>
  <div class="my-element">
    <table>
      <thead>
        <tr>
          <th v-for="(header, index) in headers" :key="index">{{ header }}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, rowIndex) in rows" :key="rowIndex">
          <td v-for="(cell, cellIndex) in row" :key="cellIndex">{{ cell }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    content: {
      type: Object,
      required: true,
      default: () => ({
        headers: ["Name", "Age", "City", "Occupation"],
        rows: [
          ["Alice", 28, "New York", "Engineer"],
          ["Bob", 34, "San Francisco", "Designer"],
          ["Charlie", 25, "Boston", "Developer"],
          ["David", 42, "Chicago", "Manager"],
          ["Eve", 29, "Los Angeles", "Artist"],
        ],
      }),
    },
  },
  computed: {
    headers() {
      return this.content.headers || [];
    },
    rows() {
      return this.content.rows || [];
    },
  },
};
</script>

<style lang="scss" scoped>
.my-element {
  table {
    width: 100%;
    border-collapse: collapse;
    th, td {
      border: 1px solid #ddd;
      padding: 8px;
    }
    th {
      background-color: #f2f2f2;
      text-align: left;
    }
    tr:nth-child(even) {
      background-color: #f9f9f9;
    }
    tr:hover {
      background-color: #ddd;
    }
  }
}
</style>
