<template>
  <IonPage id="main-page">
    <IonHeader>
      <IonToolbar color="primary">
        <IonButtons slot="start">
          <IonMenuButton></IonMenuButton>
        </IonButtons>
        <IonTitle> {{ title }} </IonTitle>
      </IonToolbar>
    </IonHeader>
    <IonContent>
      <IonRouterOutlet />
    </IonContent>
  </IonPage>
</template>

<script setup lang="ts">
  import {
    IonPage,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonRouterOutlet,
    IonButtons,
    IonMenuButton,
  } from '@ionic/vue';
  import { ref, watch } from 'vue';
  import { useRoute } from 'vue-router';

  defineOptions({
    name: 'PageLayout',
  });

  const title = ref('天使动漫论坛');
  const route = useRoute();
  watch(
    route,
    (val) => {
      if (val.meta.title) {
        title.value = val.meta.title as string;
      }
    },
    {
      immediate: true,
    },
  );
</script>

<style scoped></style>
