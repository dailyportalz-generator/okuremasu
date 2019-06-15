<template>
  <div class="okuremasuresult">
    <div class="okuremasuresult_main">
      <img src="@/assets/keitai_up.gif" alt>
      <div style="display: flex;align-items: stretch">
        <img src="@/assets/keitai_l.gif" alt>
        <div class="okuremasuresult__message">
          <!-- <p v-if="step">
            {{questions.name}} {{titleList[questions.title-1]}}
          </p> -->
          <p v-if="step === 0 ">（ここに生成された文章が表示されます）</p>
          <template v-for="(results, questionNumber) in resultsList">
            <p v-if="step > questionNumber" :key="questionNumber">
              <template v-for="(result, resultIndex) in results">
                <span :key="result" v-if="questions[`q${questionNumber+1}`] === resultIndex+1">{{result}}</span>
              </template>
            </p>
          </template>
        </div>
        <img src="@/assets/keitai_r.gif" alt>
      </div>
      <img src="@/assets/keitai_btm.gif" alt>
    </div>
  </div>
</template>

<script>
import { stringify } from 'querystring'

export default {
  props: {
    questions: Object,
    step: Number
  },
  computed: {
    // titleList() {
    //   return [ 'さま', '様', '殿', 'さん', 'くん', 'ちゃん' ]
    // },
    resultsList() {
      return [
        [
          'ご、ご、ごめんなさい！',
          'お世話になっております。申し訳ございません。',
          'いやあ、メンゴメンゴ。',
          'スミマセン。どうあやまったらいいのか分かりません。'
        ],
        [
          '８分ほど遅れてしまいそうです。',
          '20～30分遅れてしまいそうです。',
          'かなり遅れてしまいそうです。',
          'ちょ、ちょっとかなりヤバイ感じに遅れております。'
        ],
        [
          '出がけに電話でつかまっちゃって。',
          '大江戸線があんなに深いなんて。。。。',
          '思うところがあって。何もかもいやになったんです、いっしゅん。',
          'ウチのコレがコレでコレなもんで'
        ],
        [
          'いま、確かに遅れてますが、気持ちでは遅れてないつもりです。',
          'あ、いま目の前をドクター中松が歩いてきました！',
          'いや、あいつの名誉の為にも、言い訳はするまい。',
          'あれっ？ここはどこだ？'
        ],
        [
          'とにかくいそいでいますので〓すいまｓん',
          'ああああ、なにとぞご容赦くださいますようお願いいたします。',
          'いや、申し訳ないです。…………、ちくしょう、また俺の右膝が……。や、なんでもないです。',
          'あの、ほんとうにごめんなさい。「ほんとうに」なんて、何度も言ってしまったら効力ないんだけど…'
        ],
        [
          '先に行っててください。着きしだい電話します。',
          '喫茶店とかで待っててもらえると助かります。おごりますから。では。',
          'CD屋いっててください。１枚かってあげます。じゃあ。',
          '私の秘密のネコスポットを教えますので、ネコいじっててください。よろしく。'
        ]
      ]
    }
  },
  methods: {
    handleClickRestart() {
      location.href = location.href.replace(location.search, '')
    }
  }
}
</script>

<style scoped>
img {
  user-select: none;
}
form {
  width: 526px;
  margin: 0 auto;
}

.okuremasuresult {
  width: 380px;
  margin: 0 auto;
}

.okuremasuresult_main {
  font-size: 0;
}

.okuremasuresult__message {
  padding: 16px;
  font-size: 12px;
  font-weight: bold;
  flex: 1;
  min-height: 150px;
  background: #669900;
  color: #000;
}

.okuremasuresult__message p:first-child {
  margin-top: 0;
}

.okuremasuresult_build {
  text-align: right;
}

.okuremasuresult_share {
  font-size: 12px;
}

.okuremasuresult_shareurl {
  width: 100%;
}

.okuremasuresult_share {
  display: flex;
  align-items: center;
}

input {
  margin: 4px 10px 4px 0;
  flex: 1;
}
</style>