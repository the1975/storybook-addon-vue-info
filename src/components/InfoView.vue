<script>
module.exports = {
  props: {
    name: {
      type: String,
      required: true
    },
    template: {
      type: String,
      required: true
    },
    propsList: {
      type: Array,
      required: true
    },
    story: {
      type: Object
    }
  }
}
</script>

<template>
  <div class="vue-info">
    <h1 class="title">{{name}}</h1>
    <h2>Usage</h2>
    <pre class="code"><code>{{template}}</code></pre>
    <h2>Preview</h2>
    <div class="component-area">
      <slot></slot>
    </div>
    <h2>Props</h2>
    <table class="props">
      <thead class="props-head">
        <tr>
          <th>Name</th>
          <th>Type</th>
          <th>Default</th>
          <th>Description</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="prop in propsList" :key="prop.name">
          <td>
            {{prop.name}}
            <span v-if="prop.required" class="tag">required</span>
          </td>
          <td>{{prop.type}}</td>
          <td>{{prop.default}}</td>
          <td>{{prop.desc}}</td>
        </tr>
      </tbody>
    </table>
    <h2 v-if="story.events">Events</h2>
    <table class="props" v-if="story.events">
      <thead class="props-head">
      <tr>
        <th>Name</th>
        <th>Description</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="event in story.events" :key="event.name">
        <td>
          {{event.name}}
        </td>
        <td>{{event.desc}}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.vue-info {
  padding: 0 1em;
}

h1, h2, h3, h4, h5, h6 {
  color: #333;
}

h2 {
  margin-top: 2em;
}

.code {
  overflow: auto;
  padding: 1em;
  color: #fff;
  background-color: #333;
  border-radius: 3px;
}

.component-area {
  padding: 1em;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.props {
  border: 1px solid #ccc;
  border-collapse: collapse;
}

.props td, .props th {
  padding: 0.5em 1em;
  padding-right: 1.5em;
}

.props tr {
  border-bottom: 1px solid #ccc;
}

.props-head {
  color: #888;
  background-color: #eee;
  text-align: left;
}

.tag {
  font-size: 0.7em;
  padding: 0.2em 0.4em;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #eee;
  color: #333;
}
</style>
