<template>
  <div class="home">
    <h1>{{ message }}</h1>

    <!-- People List -->
    <p>counter: {{ people.length }}</p>

    <ol>
      <li v-for="person in people" v-on:click="toggleBioVisible(person)">
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
export default {
  data: function() {
    return {
      message: "People App",
      people: [
        {full_name: "Abby", bio: "likes apples", bioVisible: true},
        {full_name: "Betsy", bio: "likes buttons", bioVisible: true},
        {full_name: "Christine", bio: "likes cherries", bioVisible: true}
      ],
      newPerson: {full_name: "", bio: "", bioVisible: true}
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
    }
  },
  computed: {}
};
</script>
