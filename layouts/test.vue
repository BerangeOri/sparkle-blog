<template>
  <v-layout class="bg-amber-lighten-3">
    <v-col cols="2">
      <div class="py-10"></div>
      <v-sheet rounded="lg">
        <v-list rounded="lg">
          <v-list-item
            v-for="n in 5"
            :key="n"
            link
            :title="`List Item ${n}`"
          ></v-list-item>

          <v-divider class="my-2"></v-divider>

          <v-list-item
            color="grey-lighten-4"
            link
            title="Refresh"
          ></v-list-item>
        </v-list>
      </v-sheet>
    </v-col>
    <v-col cols="8">
      <v-app class="bg-amber-lighten-3" id="inspire">
        <v-app-bar
          flat
          prepend-icon="mdi-menu"
          scroll-behavior="hide"
          scroll-target="#target"
          scroll-threshold="150"
          class="px-3 py-1"
        >
          <v-container class="mx-auto d-flex align-center justify-center">
            <!-- <v-avatar class="me-4" color="grey-darken-1" size="32"></v-avatar> -->
            <v-btn-toggle mandatory v-model="tog" color="primary" rounded="0">
              <v-btn
                v-for="link in links"
                :key="link"
                :text="link"
                class="text-h5 mx-2"
                :to="'/' + linkRoute[link]"
              ></v-btn>
            </v-btn-toggle>

            <v-spacer></v-spacer>

            <v-responsive max-width="320">
              <v-text-field
                density="compact"
                flat
                hide-details
                label="Search"
                rounded="lg"
                single-line
                append-icon="mdi-magnify"
                variant="solo-filled"
              ></v-text-field>
            </v-responsive>
          </v-container>
        </v-app-bar>
        <v-main>
          <v-sheet
            id="target"
            class="overflow-y-auto my-5 bg-amber-lighten-3"
            max-height="90vh"
          >
            <slot />
          </v-sheet>
        </v-main>
      </v-app>
    </v-col>
    <v-col cols="2">
      <v-card>
        <v-card-title primary-title>
          이것은 카드입니다.
        </v-card-title>
        <v-btn-toggle mandatory multiple v-model="buttons">
          <v-btn prepend-icon="mdi-plus">ㅎㅇ</v-btn>
          <v-btn prepend-icon="mdi-plus">bye</v-btn>
          <v-btn prepend-icon="mdi-plus">GD</v-btn>
        </v-btn-toggle>
        <v-icon>mdi-magnify</v-icon>
      </v-card>
    </v-col>
  </v-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const tog = ref('')
const links = ref(['HOME', 'POSTS', 'GUEST', 'TAGS'])
const linkRoute = ref<Record<string, string>>({
  HOME: 'home',
  POSTS: 'post',
  GUEST: 'guest',
  TAGS: 'tag',
})

const buttons = ref([])
</script>

<style lang="scss" scoped></style>
