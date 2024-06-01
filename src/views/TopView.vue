<script setup lang="ts">
import { useRoute } from "vue-router";
import chipview from "../components/ChipView.vue";
import pview from "../components/PView.vue";

import axios from "axios";
axios
  .get(`https://igtests.sakura.ne.jp/paper_api/?num=114`)
  .then(function (response) {
    console.log(response);
  })
  .catch(function (response) {
    console.log(response);
  });
const route = useRoute();
const code = route.query.code;
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
                    text="COMPANY"
                    color="indigo"
                    variant="flat"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-office-building-outline"
                  ></chipview>
                  <pview text="SES 株式会社" class="ml-2 text-caption"></pview>
                </v-col>
              </v-row>
              <v-row :dense="true">
                <v-col cols="12">
                  <chipview
                    text="MAIL"
                    color="indigo"
                    variant="flat"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-email"
                  ></chipview>
                  <div class="ml-2">
                    <p class="mt-0">
                      <a
                        href="mailto:chiba@se-sendai.co.jp"
                        class="ml-2 text-caption"
                        >chiba@se-sendai.co.jp{{ code }}</a
                      >
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

                  <div class="ml-2 text-caption">
                    <pview
                      text="東京オフィス"
                      class="font-weight-black"
                    ></pview>
                    <pview text="〒 150-0002"></pview>
                    <pview text="東京都渋谷区渋谷3-26-16 第五叶ビル5F"></pview>
                  </div>
                  <div class="ml-2 text-caption">
                    <pview
                      text="仙台オフィス"
                      class="font-weight-black"
                    ></pview>
                    <pview text="〒 984-0051"></pview>
                    <pview text="仙台市若林区新寺2丁目1-6 THE ISビル3F"></pview>
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
                  ></chipview>
                  <div class="ml-2 text-caption">
                    <a href="https://www.se-sendai.co.jp/" target="_blank"
                      >https://www.se-sendai.co.jp/</a
                    >
                  </div>
                </v-col>
              </v-row>
              <p class="text-subtitle-1 text-center my-3 font-weight-black">
                MY PROFILE
              </p>
              <v-row :dense="true">
                <v-col cols="6">
                  <v-avatar size="100">
                    <img :src="require('@/assets/chiba.jpg')" width="100" />
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
                    <pview class="text-caption" text="開発部"></pview>
                    <pview class="text-caption" text="千葉 隆広"></pview>
                    <pview class="text-caption" text="(Takahiro Chiba)"></pview>
                  </div>
                  <div>
                    <chipview
                      text="PHONE"
                      color="indigo"
                      variant="elevated"
                      class="ma-2"
                      size="x-small"
                      icon="mdi-phone"
                    ></chipview>
                    <pview
                      class="ml-2 text-caption"
                      text="090-5846-5925"
                    ></pview>
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
                  ></chipview>
                  <pview
                    class="ml-2 text-caption"
                    text="chiba00807@gmail.com"
                  ></pview>
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
                  ></chipview>
                  <pview class="ml-2 text-caption" text="日本大学"></pview>
                </v-col>
                <v-col col="6">
                  <chipview
                    text="誕生日"
                    color="indigo"
                    variant="elevated"
                    class="ma-2"
                    size="x-small"
                    icon="mdi-home-account"
                  ></chipview>
                  <pview class="ml-2 text-caption" text="1981.8.7"></pview>
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
                  ></chipview>

                  <v-timeline side="end" class="pl-1">
                    <v-timeline-item size="small">
                      <v-alert>
                        <p class="text-caption">20xx年xx月～現在</p>
                        <p class="text-caption">営業支援システム開発</p>
                        <p class="text-caption">【言語】php / java</p>
                        <p class="text-caption">【OS】windows</p>
                        <p class="text-caption">【DB】SQL Server</p>
                        <p class="text-caption">
                          【担当】要件定義、基本設計、詳細設計、結合テスト、運用保守
                        </p>
                        <p class="text-caption">
                          【実績・取り組み】導入後も顧客へのヒアリングを継続し、随時システムを改善。また、改修を想定し、ソースコードを書き換えやすいように設計。
                        </p>
                      </v-alert>
                    </v-timeline-item>
                    <v-timeline-item size="small">
                      <v-alert>
                        <p class="text-caption">20xx年xx月～20xx年xx月</p>
                        <p class="text-caption">勘定系システム開発</p>
                        <p class="text-caption">【言語】java</p>
                        <p class="text-caption">【OS】windows</p>
                        <p class="text-caption">【DB】SQL Server</p>
                        <p class="text-caption">
                          【担当】追加機能の開発、テスト、運用保守
                        </p>
                        <p class="text-caption">
                          【実績・取り組み】システム保守の効率化のため、保守性の向上に努めました。積極的にシステムのアップデートや改善、細かいエラーのデバッグと解決に取り組むことで、保守担当エンジニアの業務改善に貢献。
                        </p>
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
                  ></chipview>

                  <p class="text-caption">
                    基本情報技術者試験 ／ 20xx年xx月合格
                  </p>
                  <p class="text-caption">
                    応用情報技術者試験 ／ 20xx年xx月合格
                  </p>
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
                  ></chipview>

                  <p class="text-caption">
                    ＜円滑にプロジェクトを進行させるマネジメント力＞
                    <br />
                    自社のプロジェクトメンバーだけでなく顧客先の関係者など、約xx名～xx名規模のプロジェクトを進めた経験があります。関係者が多くなるためスケジュールの遅延や認識齟齬が発生しないように、定期的に打ち合わせの機会を設けて進捗を管理。メンバーと顧客先との間に立ち、仕様や価格についても細かく調整、管理することで、大規模なプロジェクトも当初のスケジュールどおりに進めることができ、期日に遅れず納品することができました。
                  </p>
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
