<template>
  <v-app>
    <v-toolbar app dense>
      <v-toolbar-title class="headline text-uppercase">
        <span>Atom</span>
        <span class="font-weight-light">Lab</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn flat href="http://valdis.club/" target="_blank">
        <span class="mr-2">Home</span>
      </v-btn>
    </v-toolbar>

    <v-content>
      <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
          <v-flex xs3>
            <v-card color="white">
              <ControlPanel />
            </v-card>
          </v-flex>
          <v-flex xs9>
            <DisplayPanel />
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import ControlPanel from "./components/ControlPanel";
import DisplayPanel from "./components/DisplayPanel";

export default {
  name: "App",
  components: {
    ControlPanel,
    DisplayPanel
  },
  data() {
    return {
      //
    };
  }
};
</script>
