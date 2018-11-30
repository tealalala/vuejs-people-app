<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <!-- People List -->
    <p>counter: {{ people.length }}</p>

    Search: <input v-model="nameFilter" list="names">

    <datalist id="names">
      <span v-for="person in people">
        <option>{{ person.full_name }}</option>
        <option>{{ person.bio }}</option>
      </span>
    </datalist>

    <div class="">
      <button v-on:click="setSortAttribute('full_name')">Sort by Name</button>
      <button v-on:click="setSortAttribute('bio')">Sort by Bio</button>
    </div>

    <ol>
      <li v-for="person in orderBy(filterBy(people, nameFilter, 'full_name', 'bio'),sortAttribute, -1)"
        v-on:click="toggleBioVisible(person)">
        full_name: {{ person.full_name }},
        <p v-if="person.bioVisible">bio: {{ person.bio }}</p>
        <button v-on:click="removePerson(person.id)">Remove this Person</button>
      </li>
    </ol>


    <!-- Form to Add Person to People List -->
    <!-- <form class="" action="index.html" method="post"> -->
      <p>full_name: <input type="text" v-model="newPerson.full_name"></p>
      <p>bio: <input type="text" v-model="newPerson.bio"></p>
      <button v-on:click="addPerson()">Add Person</button>
    <!-- </form> -->

  </div>
</template>

<style>
</style>

<script>
import Vue2Filters from "vue2-filters";

export default {
  mixins: [Vue2Filters.mixin],
  data: function() {
    return {
      message: "People App",
      people: [
        {full_name: "Abby", bio: "loves apples", bioVisible: true},
        {full_name: "Betsy", bio: "likes buttons", bioVisible: true},
        {full_name: "Christine", bio: "likes cherries", bioVisible: true}
      ],
      newPerson: {full_name: "", bio: "", bioVisible: true},
      nameFilter: '',
      sortAttribute: ''
    };
  },
  created: function() {},
  methods: {
    addPerson: function() {
      console.log("add person button");
      this.people.push(this.newPerson);
      this.newPerson = {full_name: "", bio: "", bioVisible: true};
    },
    removePerson: function(inputPerson) {
      var index = this.people.indexOf(inputPerson);
      this.people.pop(index);
    },
    toggleBioVisible: function (inputPerson) {
      console.log('toggle bioVisible');
      inputPerson.bioVisible = !inputPerson.bioVisible;
      // var liTag = document.querySelector('li');
      // liTag.classList.toggle('hidden');
    },
    setSortAttribute: function(inputAttribute) {
      this.sortAttribute = inputAttribute;
    }
  },
  computed: {}
};
</script>
