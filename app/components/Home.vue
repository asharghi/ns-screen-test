<template>
  <Page>
    <ActionBar>
      <Label text="Home" />
    </ActionBar>

    <StackLayout margin="10">
      <GridLayout rows="auto" columns="*,auto">
        <Label fontSize="20" text="WidthDIPs" />
        <Label fontSize="20" :text="widthDIPs" col="1" />
      </GridLayout>
      <GridLayout rows="auto" columns="*,auto">
        <Label fontSize="20" text="HeightDIPs" />
        <Label fontSize="20" :text="heightDIPs" col="1" />
      </GridLayout>
      <GridLayout rows="auto" columns="*,auto">
        <Label fontSize="20" text="WidthPixels" />
        <Label fontSize="20" :text="widthPixels" col="1" />
      </GridLayout>
      <GridLayout rows="auto" columns="*,auto">
        <Label fontSize="20" text="HeightPixels" />
        <Label fontSize="20" :text="heightPixels" col="1" />
      </GridLayout>
      <GridLayout rows="auto" columns="*,auto">
        <Label fontSize="20" text="Scale" />
        <Label fontSize="20" :text="scale" col="1" />
      </GridLayout>
    </StackLayout>
  </Page>
</template>

<script>
import { Screen, Application, Dialogs } from "@nativescript/core";
export default {
  data() {
    return {
      widthDIPs: 0,
      heightDIPs: 0,
      widthPixels: 0,
      heightPixels: 0,
      scale: 0,
    };
  },
  methods: {
    setScreenInfo() {
      this.widthDIPs = Screen.mainScreen.widthDIPs;
      this.heightDIPs = Screen.mainScreen.heightDIPs;
      this.widthPixels = Screen.mainScreen.widthPixels;
      this.heightPixels = Screen.mainScreen.heightPixels;
      this.scale = Screen.mainScreen.scale;
      return {
        widthDIPs: this.widthDIPs,
        heightDIPs: this.heightDIPs,
        widthPixels: this.widthPixels,
        heightPixels: this.heightPixels,
        scale: this.scale,
      };
    },
  },
  mounted() {
    Application.on(Application.resumeEvent, () => {
      const result = this.setScreenInfo();
      Dialogs.alert({
        title: "Resume",
        message: JSON.stringify(result),
        okButtonText: "OK",
      });
    });
  },
};
</script>
