<script setup lang="ts">
import { ref } from "vue";
import { useRoute } from "vue-router";
import chipview from "../components/ChipView.vue";
import pview from "../components/PView.vue";

import axios from "axios";

const route = useRoute();
const code = route.query.code;
const url = "https://paper.rash.jp/paper_api/?code=" + code;
const company = ref("");
const mail = ref("");
const company_link = ref("");
const profImage = ref("");
const company_address = ref();
const profposition = ref();
const profname = ref();
const profkana = ref();
const phone = ref();
const email = ref();
const from = ref();
const birth = ref();
const history = ref();
const skill = ref();
const pr = ref();
axios
  .get(url, {
    headers: {
      "Content-Type": "application/json",
      "Access-Control-Allow-Origin": "*",
    },
  })
  .then(function (response) {
    console.log(response);
    let body = response["data"]["body"];
    company.value = body["company"];
    mail.value = body["mail"];
    company_address.value = body["company_address"];
    company_link.value = body["company_link"];
    profImage.value = body["profImage"];
    profposition.value = body["profposition"];
    profname.value = body["profname"];
    profkana.value = body["profkana"];
    phone.value = body["phone"];
    email.value = body["email"];
    from.value = body["from"];
    birth.value = body["birth"];
    history.value = body["history"];
    skill.value = body["skill"];
    pr.value = body["pr"];
  })
  .catch(function (response) {
    console.log("error");
    console.log(response);
  });

const onClick = (url: string) => {
  location.href = url;
};
</script>
<template>
  <v-main>
    <v-container class="py-1 px-6" fluid>
      <v-toolbar color="primary" density="compact">
        <v-spacer></v-spacer>
        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-download</v-icon>
        </v-btn>
        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-toolbar>
      <v-row>
        <v-col cols="12">
          <v-card>
            <v-sheet color="white lighten-4" class="pa-4">
              <v-row :dense="true">
                <v-col cols="6">
                  <img :src="require('@/assets/ses.png')" width="100" />
                </v-col>
                <v-col cols="6">
                  <chipview
                    v-if="company"
                    text="COMPANY"
                    color="indigo"
                    variant="flat"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-office-building-outline"
                  ></chipview>
                  <pview :text="company" class="ml-2 text-caption"></pview>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col cols="12">
                  <chipview
                    v-if="mail"
                    text="MAIL"
                    color="indigo"
                    variant="flat"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-email"
                  ></chipview>
                  <div class="ml-2">
                    <p class="mt-0">
                      <a :href="`mailto:` + mail" class="ml-2 text-caption">{{
                        mail
                      }}</a>
                    </p>
                  </div>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col cols="12">
                  <chipview
                    text="COMPANY ADDRESS"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-domain"
                  ></chipview>

                  <div
                    class="ml-2 text-caption"
                    v-for="value in company_address"
                    :key="value"
                  >
                    <pview :text="value.name" class="font-weight-black"></pview>
                    <pview :text="value.post"></pview>
                    <pview :text="value.address"></pview>
                  </div>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col cols="12">
                  <chipview
                    text="COMPANY LINK"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-link-box"
                    v-if="company_link"
                  ></chipview>
                  <div class="ml-2 text-caption">
                    <a :href="company_link" target="_blank">{{
                      company_link
                    }}</a>
                  </div>
                </v-col>
              </v-row>
              <p class="text-subtitle-1 text-center my-3 font-weight-black">
                MY PROFILE
              </p>
              <v-row :dense="true">
                <v-col cols="6">
                  <v-avatar size="100">
                    <img :src="profImage" width="100" />
                  </v-avatar>
                </v-col>
                <v-col cols="6">
                  <div>
                    <chipview
                      text="NAME"
                      color="indigo"
                      variant="elevated"
                      class="ma-2"
                      size="x-small"
                      icon="mdi-account-circle"
                    ></chipview>
                    <pview class="text-caption" :text="profposition"></pview>
                    <pview class="text-caption" :text="profname"></pview>
                    <pview class="text-caption" :text="profkana"></pview>
                  </div>
                  <div>
                    <chipview
                      text="PHONE"
                      color="indigo"
                      variant="elevated"
                      class="ma-2"
                      size="x-small"
                      icon="mdi-phone"
                      v-if="phone"
                    ></chipview>
                    <pview class="ml-2 text-caption" :text="phone"></pview>
                  </div>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col col="12" class="pa-0">
                  <chipview
                    text="メールアドレス"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-mail"
                    v-if="email"
                  ></chipview>
                  <pview class="ml-2 text-caption" :text="email"></pview>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col col="6">
                  <chipview
                    text="出身地・出身校"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-home-account"
                    v-if="from"
                  ></chipview>
                  <pview class="ml-2 text-caption" :text="from"></pview>
                </v-col>
                <v-col col="6">
                  <chipview
                    text="誕生日"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-home-account"
                    v-if="birth"
                  ></chipview>
                  <pview class="ml-2 text-caption" :text="birth"></pview>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col cols="12">
                  <chipview
                    text="経歴"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-history"
                    v-if="history"
                  ></chipview>

                  <v-timeline side="end" class="pl-1">
                    <v-timeline-item
                      size="small"
                      v-for="value in history"
                      :key="value"
                    >
                      <v-alert>
                        <p class="text-caption html" v-text="value.note"></p>
                      </v-alert>
                    </v-timeline-item>
                  </v-timeline>
                </v-col>
              </v-row>

              <v-row :dense="true">
                <v-col col="6">
                  <chipview
                    text="テクニカルスキル"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-home-account"
                    v-if="skill"
                  ></chipview>

                  <p class="text-caption html" v-text="skill"></p>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col col="6">
                  <chipview
                    text="自己PR"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-home-account"
                    v-if="pr"
                  ></chipview>

                  <p class="text-caption html" v-text="pr"></p>
                </v-col>
              </v-row>

              <hr class="my-3" />
              <v-row>
                <v-col cols="3">
                  <v-btn
                    icon="mdi-twitter"
                    @click="onClick('https://x.com/XCObWyo11N7MdPj')"
                  ></v-btn>
                </v-col>
                <v-col cols="3">
                  <v-btn
                    icon="mdi-chat"
                    @click="
                      onClick(
                        'https://social-plugins.line.me/lineit/share?url=http://chiba00807.starfree.jp/'
                      )
                    "
                  ></v-btn>
                </v-col>
                <v-col cols="3">
                  <v-btn
                    icon="mdi-facebook"
                    @click="
                      onClick('https://www.facebook.com/takahiro.chiba.37')
                    "
                  ></v-btn>
                </v-col>
                <v-col cols="3">
                  <v-btn
                    icon="mdi-instagram "
                    @click="onClick('https://www.instagram.com/chiba00807/')"
                  ></v-btn>
                </v-col>
              </v-row>
            </v-sheet>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>
<style>
.html {
  white-space: pre-wrap;
}
</style>
