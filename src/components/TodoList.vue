<template>
  <h1 class="text-xl font-medium text-black">Task Tracker</h1>
  <div class="w-50">
    <input
      v-model="title"
      type="text"
      style="
        border: 1px solid #ccc;
        border-radius: 4px;
        padding: 12px;
        margin: 5px 0;
      "
      placeholder="Title"
    />
    <br />
    <input
      v-model="description"
      type="text"
      placeholder="Description"
      style="border: 1px solid #ccc; border-radius: 4px; padding: 12px"
    />
    <br />
    <button
      @click.prevent="submit"
      class="bg-black p-2 m-5"
      style="color: #fff"
    >
      Add
    </button>
  </div>
  <hr />
  <ul v-for="(item, i) in data" :key="i">
    <li>
      {{ i }} Title: {{ item.title }}
      <button class="bg-black p-2 m-5" style="color: #fff" @click="edit(i)">
        Edit
      </button>
      <button class="bg-black p-2 m-5" style="color: #fff" @click="remove(i)">
        Delete
      </button>
    </li>
    <li>Description: {{ item.description }}</li>
    <hr />
  </ul>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      title: null,
      description: null,
      data: [],
    };
  },
  methods: {
    submit() {
      const temp = {
        title: this.title,
        description: this.description,
      };
      this.title = null;
      this.description = null;
      this.data.push(temp);
      console.log(this.data);
    },
    edit(index) {
      this.title = this.data[index].title;
      this.description = this.data[index].description;
    },
    remove(index) {
      this.data.splice(index, 1);
    },
  },
};
</script>
