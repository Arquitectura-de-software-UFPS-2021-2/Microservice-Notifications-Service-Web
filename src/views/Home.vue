<template>
  <div>
    <v-app>
      <v-container>
        <v-layout :wrap="true">
          <v-flex xs12>
            <v-card color="error" dark>
              <v-card-text class="display-1 text-center">
                Notificaciones &nbsp; <v-icon>notifications</v-icon>
              </v-card-text>
            </v-card>

            <v-card>
              <v-container fluid>
                <v-row justify="center">
                  <v-subheader v-if="notifications.data"
                    >Bandeja de Notificaciones</v-subheader
                  >
                  <v-subheader v-else
                    >No hay notificaciones disponibles</v-subheader
                  >

                  <v-expansion-panels popout>
                    <v-expansion-panel
                      v-for="(item, i) in notifications.data"
                      :key="i"
                      hide-actions
                    >
                      <v-expansion-panel-header>
                        <v-row align="center" class="spacer" no-gutters>
                          <v-col cols="4" sm="2" md="1">
                            <v-avatar size="36px">
                              <v-btn
                                v-if="item.id_type === 5"
                                color="primary"
                                fab
                              >
                                <v-icon> account_circle </v-icon>
                              </v-btn>

                              <v-btn
                                v-if="item.id_type === 4"
                                color="warning"
                                fab
                              >
                                <v-icon> engineering </v-icon>
                              </v-btn>

                              <v-btn
                                v-if="item.id_type === 7"
                                color="success"
                                fab
                              >
                                <v-icon> school </v-icon>
                              </v-btn>

                              <v-btn
                                v-if="item.id_type === 3"
                                color="purple_ligth"
                                fab
                              >
                                <v-icon> event </v-icon>
                              </v-btn>

                              <v-btn
                                v-if="item.id_type === 6"
                                color="sky"
                                fab
                              >
                                <v-icon> loyalty </v-icon>
                              </v-btn>

                              <v-btn
                                v-if="item.id_type === 1"
                                color="accent"
                                fab
                              >
                                <v-icon> connect_without_contact </v-icon>
                              </v-btn>

                              <v-btn
                                v-if="item.id_type === 2"
                                color="secondary"
                                fab
                              >
                                <v-icon> person_add_alt </v-icon>
                              </v-btn>
                            </v-avatar>
                          </v-col>

                          <v-col class="hidden-xs-only" sm="5" md="3">
                            <strong v-html="item.title"></strong>
                          </v-col>

                          <v-col class="text-no-wrap" cols="5" sm="3">
                            <v-chip
                              v-if="item.id_state === 1"
                              :color="`error lighten-4`"
                              class="ml-0 mr-2 black--text"
                              label
                              small
                            >
                              Sin leer
                            </v-chip>

                            <v-chip
                              v-if="item.id_state === 2"
                              :color="`primary lighten-4`"
                              class="ml-0 mr-2 black--text"
                              label
                              small
                            >
                              Leido
                            </v-chip>
                          </v-col>

                          <v-col
                            v-if="item.title"
                            class="grey--text text-truncate hidden-sm-and-down"
                          >
                            <timeago :datetime="item.create_date"></timeago>
                            &nbsp;
                            <v-icon>history_toggle_off</v-icon>
                          </v-col>
                        </v-row>
                      </v-expansion-panel-header>

                      <v-expansion-panel-content>
                        <v-divider></v-divider>
                        <v-card-text v-text="item.description"></v-card-text>
                      </v-expansion-panel-content>
                    </v-expansion-panel>
                  </v-expansion-panels>
                </v-row>
              </v-container>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-app>
  </div>
</template>

<script>
import axios from "axios";
import { mapMutations } from "vuex";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      notifications: "",
      id:''
    };
  },
  methods: {
    ...mapMutations(["mostrarLoading", "ocultarLoading"]),
    async getNotifications(id) {
      try {
        this.mostrarLoading({
          titulo: "Accediendo a la informacion",
          color: "error",
        });
        this.notifications = await axios.post(
          "http://localhost:4000/verNotificaciones",
          {
            id_user: id,
          }
        );

        console.log(this.notifications.data);
      } catch (error) {
        console.log("Error al consumir API" + error);
      } finally {
        this.ocultarLoading();
      }
      //
    },
  },
  beforeMount(){
    const urlParams = new URLSearchParams(window.location.search);
    this.id = urlParams.get("id");
  },
  mounted() {
    this.getNotifications(this.id);
  }
  
};
</script>
