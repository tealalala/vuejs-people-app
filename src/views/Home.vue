<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <ol>
      <li v-for="person in people">
        name: {{ person.name }},
        bio: {{ person.bio }},
        bioVisible: {{ person.bioVisible }}
      </li>
    </ol>


  </div>
</template>

<style>
</style>

<script>
export default {
  data: function() {
    return {
      message: "People App",
      people: [
        {name: "Abby", bio: "likes apples", bioVisible: true},
        {name: "Christine", bio: "likes cherries", bioVisible: true},
        {name: "Dalena", bio: "likes danishes", bioVisible: true}
      ]
    };
  },
  created: function() {},
  methods: {},
  computed: {}
};
</script>
