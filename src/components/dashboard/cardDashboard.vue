<template>
  <v-card class="mx-auto" max-width="368">
    <v-tooltip location="bottom" :text="title">
      <template v-slot:activator="{ props }">
        <v-card-title v-bind="props" class="text-truncate">
          {{ truncate(title, 20) }}
        </v-card-title>
      </template>
    </v-tooltip>
    <v-card-subtitle class="pb-0">
      <v-icon
        class="me-1 pb-1"
        color="warning"
        icon="mdi mdi-information"
        size="18"
      ></v-icon>
      {{ description }}
    </v-card-subtitle>

    <v-card-text class="py-3">
      <v-row align="center" no-gutters>
        <v-col :class="sizeResult ? sizeResult : 'text-h2'" cols="6">
          {{ result }}
        </v-col>
        <v-col class="text-right" cols="6">
          <v-icon color="error" :icon="icon" size="65"></v-icon>
        </v-col>
      </v-row>
    </v-card-text>
    <v-divider></v-divider>
    <div class="d-flex py-3">
      <v-list-item density="compact" prepend-icon="mdi mdi-alarm">
        <v-list-item-subtitle>Atualizado em {{ date }}</v-list-item-subtitle>
      </v-list-item>
    </div>
  </v-card>
</template>

<script setup lang="ts">
defineProps<{
  title: string;
  description: string;
  icon: string;
  result: string;
  date: string;
  sizeResult?: string;
}>();

const truncate = (text: string, length: number) => {
  return text.length > length ? text.substring(0, length) + "..." : text;
};
</script>

<style scoped>
.text-truncate {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>
