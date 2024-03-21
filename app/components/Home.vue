<template>
  <Page>
    <ActionBar>
      <Label text="Home" />
    </ActionBar>

    <StackLayout margin="10" :key="updateKey">
      <GridLayout rows="auto" columns="*,auto">
        <Label fontSize="20" text="Update count" />
        <Label fontSize="20" :text="updateCount" col="1" />
      </GridLayout>
    </StackLayout>
  </Page>
</template>

<script>
import { Application } from "@nativescript/core";
export default {
  data() {
    return {
      updateCount: 0,
    };
  },
  mounted() {
    Application.on(Application.resumeEvent, () => {
      this.updateCount += 1;
    });
  },
};
</script>
