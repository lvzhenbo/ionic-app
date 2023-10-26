<template>
  <IonPage>
    <IonContent>
      <IonCard>
        <IonCardHeader>
          <IonCardTitle>论坛分区</IonCardTitle>
        </IonCardHeader>
        <IonCardContent>
          <IonGrid>
            <IonRow>
              <IonCol v-for="item in groupList" :key="item.gid" size="6">
                <IonButton
                  :router-link="`/forum/${item.gid}`"
                  expand="block"
                  fill="clear"
                  class="text-black"
                >
                  {{ item.title }}
                </IonButton>
              </IonCol>
            </IonRow>
          </IonGrid>
        </IonCardContent>
      </IonCard>
    </IonContent>
  </IonPage>
</template>

<script setup lang="ts">
  import { forumGroup } from '@/api/forum';
  import { onMounted, ref } from 'vue';
  import {
    IonPage,
    IonContent,
    IonCard,
    IonCardHeader,
    IonCardContent,
    IonCardTitle,
    IonGrid,
    IonRow,
    IonCol,
    IonButton,
  } from '@ionic/vue';

  interface Group {
    gid: number;
    title: string;
  }

  defineOptions({
    name: 'HomeIndex',
  });

  const groupList = ref<Group[]>([]);

  onMounted(() => {
    getForumGroup();
  });

  async function getForumGroup() {
    try {
      const res = await forumGroup();
      if (res.data) {
        const data = JSON.parse(res.data);
        if (data.status === 0) {
          groupList.value = data.group;
        }
      }
    } catch (error) {
      console.error(error);
    }
  }
</script>

<style scoped></style>
