<template>
  <v-card max-width="448" class="mx-auto" color="grey-lighten-4">
    <v-layout>
      <v-app-bar color="teal-darken-4" class="text-white">
        <v-app-bar-nav-icon> </v-app-bar-nav-icon>
        <v-app-bar-title> PhraseBook </v-app-bar-title>
      </v-app-bar>

      <v-main>
        <v-container fluid>
          <img width="80" height="80" src="/icons/ir.svg" alt="Farsi" />

          <v-row v-if="phrases" dense>
            <v-col v-for="item in phrases" :key="item.id" cols="12">
              <v-card :title="item.tr.text">
                <v-card-header>
                  <v-card-avatar> </v-card-avatar>

                  <v-card-header-text>
                    <v-card-title>{{ item.tr.text }}</v-card-title>

                    <v-card-subtitle>{{ item.tr.text }}</v-card-subtitle>
                  </v-card-header-text>
                </v-card-header>

                <v-card-text>
                  <h4>
                    {{ item.tr.text }}
                  </h4>
                  <h4>
                    {{ item.fa.text }}
                  </h4>
                  <h4>
                    {{ item.en.text }}
                  </h4>
                </v-card-text>
                <v-card-actions>
                  <v-btn>Action 1</v-btn>

                  <v-btn>Action 2</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
    </v-layout>
  </v-card>
</template>
<script>
import axios from "axios";
const dataJsonPath = "https://temsool.com/app/phrasebook/phrases.json";
export default {
  name: "HomePage",
  async created() {
    try {
      const res = await axios.get(dataJsonPath);

      this.phrases = res.data.phrases;
      console.log(this.phrases);
    } catch (error) {
      console.log(error);
    }
  },
  data() {
    return {
      phrases: [],
      publicPath: process.env.BASE_URL,
    };
  },
  components: [axios],
};
</script>