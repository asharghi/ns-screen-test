<template>
  <Page>
    <ActionBar>
      <Label text="Home" />
    </ActionBar>
    <StackLayout>
      <GridLayout margin="10" rows="auto" columns="*,auto">
        <Label fontSize="20" text="Update count" />
        <Label fontSize="20" :text="updateCount" col="1" />
      </GridLayout>
      <Button @tap="update" text="Add 1" />
    </StackLayout>
  </Page>
</template>

<script>
export default {
  data() {
    return {
      updateCount: 0,
    };
  },
  methods: {
    update() {
      this.updateCount++;
    },
  },
};
</script>
