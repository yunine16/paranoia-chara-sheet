<template>
  <v-container>
    <v-row class="text-center" justify="center">
      <p>超簡易的なパラノイア用キャラシ作成ツール</p>
    </v-row>
    <v-row class="text-center" justify="center">
      <v-col cols="8">
        <h1>パーソナルデータ</h1>
        <v-data-table :headers="personalDataTableHeaders" :items="personalDataTableItems" hide-default-footer>
          <template v-slot:item.personalData="props">
            <v-edit-dialog :return-value.sync="props.item.personalData">
              {{ props.item.personalData }}
              <template v-slot:input>
                <v-text-field v-model="props.item.personalData" single-line />
              </template>
            </v-edit-dialog>
          </template>
        </v-data-table>
      </v-col>
    </v-row>
    <v-row class="text-center" justify="center">
      <v-col cols="8">
        <h1>秘密情報</h1>
        <v-data-table :headers="secretPersonalDataTableHeaders" :items="secretPersonalDataTableItems" hide-default-footer>
          <template v-slot:item.secretPersonalData="props">
            <v-edit-dialog :return-value.sync="props.item.secretPersonalData">
              {{ props.item.secretPersonalData }}
              <template v-slot:input>
                <v-text-field v-model="props.item.secretPersonalData" single-line />
              </template>
            </v-edit-dialog>
          </template>
        </v-data-table>
      </v-col>
    </v-row>
    <v-row class="text-center" justify="center">
      <v-col cols="5" md="4" v-for="state in status" :key="state.id">
        <h1>{{ state.text }}</h1>
        <v-select :items=[4,5,6,7,8,9,10] v-model="state.point"></v-select>
        <v-data-table :headers="tableHeaders" :items="tableItems[state.id-1]" hide-default-footer>
          <template v-slot:item.specialty="props">
            <v-checkbox v-model="props.item.specialty"></v-checkbox>
          </template>
          <template v-slot:item.weakness="props">
            <v-checkbox v-model="props.item.weakness"></v-checkbox>
          </template>
          <template v-slot:item.point="props">
            <v-edit-dialog :return-value.sync="props.item.point">
              {{ props.item.point }}
              <template v-slot:input>
                <v-text-field v-model.number="props.item.point" type="Number" single-line />
              </template>
            </v-edit-dialog>
          </template>
        </v-data-table>
      </v-col>
    </v-row>
    <v-row class="text-center" justify="center">
      <v-col cols="8">
        <h1>秘密技能</h1>
        <v-data-table :headers="secretSkillTableHeaders" :items="secretSkillTableItems" hide-default-footer>
          <template v-slot:item.secretSkill="props">
            <v-edit-dialog :return-value.sync="props.item.secretSkill">
              {{ props.item.secretSkill }}
              <template v-slot:input>
                <v-text-field v-model="props.item.secretSkill" single-line />
              </template>
            </v-edit-dialog>
          </template>
        </v-data-table>
      </v-col>
    </v-row>
    <v-row class="text-center" justify="center">
      <v-col cols="8">
        <h2>チャットパレット</h2>
        <p>ここをコピーしてね</p>
        <v-text-field v-model="chatParet"></v-text-field>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',


    data: () => ({
      personalDataTableHeaders: [
        { text: "名前", value: "name" },
        { text: "データ", value: "personalData" },
      ],
      personalDataTableItems: [
        { name: "キャラクター名", personalData: "" },
        { name: "サービスグループ", personalData: "" },
        { name: "癖", personalData: "" },
      ],
      secretPersonalDataTableHeaders: [
        { text: "名前", value: "name" },
        { text: "データ", value: "secretPersonalData" },
      ],
      secretPersonalDataTableItems: [
        { name: "秘密結社", secretPersonalData: "" },
        { name: "ミュータント能力", secretPersonalData: "" },
      ],
      status: [
        { id: 1, name: "management", text: "マネジメント", point: 0 },
        { id: 2, name: "stealth", text: "ステルス", point: 0 },
        { id: 3, name: "violence", text: "バイオレンス", point: 0 },
        { id: 4, name: "hardware", text: "ハードウェア", point: 0 },
        { id: 5, name: "software", text: "ソフトウェア", point: 0 },
        { id: 6, name: "wetware", text: "ウェットウェア", point: 0 },
      ],
      tableHeaders: [
        { text: "技能名", value: "name" },
        { text: "専門", value: "specialty" },
        { text: "弱点", value: "weakness" },
        { text: "判定", value: "point" }
      ],
      tableItems: [
        [
          { name: "靴舐め", specialty: false, weakness: false, point: 0 },
          { name: "鉄面皮", specialty: false, weakness: false, point: 0 },
          { name: "詐術", specialty: false, weakness: false, point: 0 },
          { name: "衛生管理", specialty: false, weakness: false, point: 0 },
          { name: "尋問", specialty: false, weakness: false, point: 0 },
          { name: "脅迫", specialty: false, weakness: false, point: 0 },
          { name: "見定め", specialty: false, weakness: false, point: 0 },
          { name: "雄弁術", specialty: false, weakness: false, point: 0 },
        ],
        [
          { name: "隠匿", specialty: false, weakness: false, point: 0 },
          { name: "変装", specialty: false, weakness: false, point: 0 },
          { name: "厳戒", specialty: false, weakness: false, point: 0 },
          { name: "セキュリティシステム", specialty: false, weakness: false, point: 0 },
          { name: "尾行", specialty: false, weakness: false, point: 0 },
          { name: "手業", specialty: false, weakness: false, point: 0 },
          { name: "隠密", specialty: false, weakness: false, point: 0 },
          { name: "監視", specialty: false, weakness: false, point: 0 },
        ],
        [
          { name: "敏捷", specialty: false, weakness: false, point: 0 },
          { name: "爆破", specialty: false, weakness: false, point: 0 },
          { name: "エネルギー兵器", specialty: true, weakness: false, point: 0 },
          { name: "フィールド兵器", specialty: false, weakness: false, point: 0 },
          { name: "精密作業", specialty: false, weakness: false, point: 0 },
          { name: "白兵戦武器", specialty: false, weakness: false, point: 0 },
          { name: "射出兵器", specialty: false, weakness: false, point: 0 },
          { name: "投擲武器", specialty: false, weakness: false, point: 0 },
          { name: "格闘", specialty: false, weakness: false, point: 0 },
          { name: "車両戦闘", specialty: false, weakness: false, point: 0 },
        ],
        [
          { name: "ボット運用", specialty: false, weakness: false, point: 0 },
          { name: "化学工学", specialty: false, weakness: false, point: 0 },
          { name: "電子工学", specialty: false, weakness: false, point: 0 },
          { name: "環境工学", specialty: false, weakness: false, point: 0 },
          { name: "機械工学", specialty: false, weakness: false, point: 0 },
          { name: "核工学", specialty: false, weakness: false, point: 0 },
          { name: "重機操作", specialty: false, weakness: false, point: 0 },
          { name: "車両運用", specialty: false, weakness: false, point: 0 },
          { name: "装備保守", specialty: false, weakness: false, point: 0 },
        ],
        [
          { name: "ボットプログラミング", specialty: false, weakness: false, point: 0 },
          { name: "C-Bay", specialty: false, weakness: false, point: 0 },
          { name: "データ分析", specialty: false, weakness: false, point: 0 },
          { name: "データ検索", specialty: false, weakness: false, point: 0 },
          { name: "金融システム", specialty: false, weakness: false, point: 0 },
          { name: "ハッキング", specialty: false, weakness: false, point: 0 },
          { name: "マルチコーダー運用", specialty: false, weakness: false, point: 0 },
          { name: "オペレーティングシステム", specialty: false, weakness: false, point: 0 },
          { name: "車両プログラミング", specialty: false, weakness: false, point: 0 },
        ],
        [
          { name: "生命科学", specialty: false, weakness: false, point: 0 },
          { name: "生物兵器", specialty: false, weakness: false, point: 0 },
          { name: "クローン技術", specialty: false, weakness: false, point: 0 },
          { name: "医学", specialty: false, weakness: false, point: 0 },
          { name: "アウトドア知識", specialty: false, weakness: false, point: 0 },
          { name: "薬物療法", specialty: false, weakness: false, point: 0 },
          { name: "心理療法", specialty: false, weakness: false, point: 0 },
          { name: "暗示", specialty: false, weakness: false, point: 0 },
        ],
      ],
      secretSkillTableHeaders: [
        { text: "カテゴリ", value: "category" },
        { text: "秘密技能", value: "secretSkill" }
      ],
      secretSkillTableItems: [
        { category: "非日常", secretSkill: "" },
        { category: "不要", secretSkill: "" },
        { category: "不健全", secretSkill: ""}
      ]
    }),
    methods: {
      setStatusPoint(num, point) {
        for(const item of this.tableItems[num-1]) {
          item.point = point;

          if(item.specialty) {
            item.point += 4;
          }

          if(item.weakness) {
            item.point -= 5;
          }
        }
      }
    },
    computed: {
      chatParet() {
        let chatText ="";
        for(const items of this.tableItems) {
          for(const item of items) {
            chatText += "1d20<=" + item.point + "【" + item.name + "】";
          }
        }
        return chatText;
      }
    },
    watch: {
      status: {
        handler: function() {
          for(const state of this.status) {
            if(state.point) {
              if(state.point > 3 && state.point < 11) {
                const stateNum = state.id;
                const statePoint = Number(state.point);
                this.setStatusPoint(stateNum, statePoint);
              } else {
                alert("基礎値は4以上10以下の値に設定してください");
              }
            }
          }
        },
        deep: true
      },
      tableItems: {
        handler: function() {
          console.log('kuso');
          for(const state of this.status) {
            const stateNum = state.id;
            const statePoint = Number(state.point);
            console.log(typeof(statePoint));
            this.setStatusPoint(stateNum, statePoint);
          }
        }
      }
    }
  }
</script>
