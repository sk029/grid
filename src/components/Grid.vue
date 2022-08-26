<script setup>
 const props = defineProps({
    rows: {
        type: Number,
        required: true
    },
    columns: {
        type: Number,
        required: true
    },
})
</script>

<template>
<table>
      <tbody>
        <tr v-for="row in rows">
          <td v-for="col in columns">
            [{{ row }} x {{ col }}]
          </td>
        </tr>
      </tbody>
    </table>
</template>

<style>
</style>