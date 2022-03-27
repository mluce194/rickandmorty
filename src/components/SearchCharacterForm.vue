<template>
  <p class="text-lg p-8 text-[#60a1c9] font-bold">
    Use our search form below to find information about a Rick & Morty character
  </p>

  <div v-if="error">Sorry, an error occured...</div>
  <div v-if="loading">Loading...</div>

  <div v-else class="w-4/5 mx-auto border-solid">
    <form>
      <label for="texte" class="block m-2"
        >Search for a specific character</label
      >
      <input
        type="text"
        v-model="inputCharacter"
        placeholder="Enter character name"
      />
    </form>

    <!-- Character card start -->
    <div class="w-full mx-auto border-solid flex flex-wrap justify-around">
      <div
        class="max-w-md py-4 px-8 bg-white shadow-lg rounded-lg my-20"
        v-for="character in result.characters.results"
        :key="character.id"
        v-show="checkCharacter(inputCharacter, character.name)"
      >
        <div class="flex justify-center md:justify-end -mt-16">
          <img
            class="w-20 h-20 object-cover rounded-full border-2 border-[#99cae9]"
            :src="`${character.image}`"
            :alt="`${character.name}`"
          />
        </div>
        <div>
          <h2 class="text-gray-800 text-3xl font-semibold">
            {{ character.name }}
          </h2>
          <p class="mt-2 text-gray-600">
            <strong>Gender</strong> : {{ character.gender }}
          </p>

          <p class="mt-2 text-gray-600">
            <strong>Origin</strong> : {{ character.origin.name }}
          </p>
          <p class="mt-2 text-gray-600">
            <strong>Episodes</strong> :
            <span
              class="mt-2 text-gray-600 after:content-['-'] last:after:content-['']"
              v-for="episode in character.episode"
              :key="episode"
              >{{ episode.episode }}</span
            >
          </p>
        </div>
        <div class="flex justify-end mt-4">
          <a href="#" class="text-xl font-medium text-[#99cae9]"
            >Status : {{ character.status }}</a
          >
        </div>
      </div>
    </div>
    <!-- Character card end -->
  </div>
</template>

<script>
import gql from "graphql-tag";
import { useQuery } from "@vue/apollo-composable";

const CHARACTERS_QUERY = gql`
  query Characters {
    characters {
      results {
        image
        name
        origin {
          name
        }
        gender
        status
        episode {
          episode
        }
        id
      }
    }
  }
`;

export default {
  name: "SearchCharacterForm",
  setup() {
    const { result, loading, error } = useQuery(CHARACTERS_QUERY);
    return {
      result,
      loading,
      error,
    };
  },
  data() {
    return {
      inputCharacter: "",
    };
  },
  methods: {
    checkCharacter(input, character) {
      if (character.toLowerCase().startsWith(input.toLowerCase())) {
        return true;
      }
    },
  },
};
</script>
