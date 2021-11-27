<template>
  <div id="extractor">

    <div class="column is-6 is-offset-3">
      <h2 class="subtitle">Text </h2>
    </div>
      <div class="column is-6 is-offset-3">
        <textarea class="textarea is-link" placeholder="10 lines of textarea" rows="10" v-model="text"></textarea>
      </div>


      <div class="control column is-6 is-offset-3">
        <p>案例标题</p>
        <div class="notification is-primary" >
          <span style="white-space: pre-wrap" v-for="value in title" v-bind:key = value>{{value}}</span>
        </div>
      </div>

    <div class="control column is-6 is-offset-3">
      <p>事故案例</p>
      <div class="notification is-primary" >
        <span style="white-space: pre-wrap" v-for="value in story" v-bind:key = value>{{value}}</span>
      </div>
    </div>

    <div class="control column is-6 is-offset-3">
      <p>事故原因</p>
      <div class="notification is-link" >
        <span style="white-space: pre-wrap" v-for="value in reason0" v-bind:key = value>{{value}}</span>
      </div>
    </div>

    <div class="control column is-6 is-offset-3">
      <p>直接原因</p>
      <div class="notification is-link" >
        <span style="white-space: pre-wrap" v-for="value in reason1" v-bind:key = value>{{value}}</span>
      </div>
    </div>

    <div class="control column is-6 is-offset-3">
      <p>间接原因</p>
      <div class="notification is-info" >
        <span style="white-space: pre-wrap" v-for="value in reason2" v-bind:key = value>{{value}}</span>
      </div>
    </div>


    <div class="control column is-6 is-offset-3">
      <p>主要原因</p>
      <div class="notification is-info" >
        <span style="white-space: pre-wrap" v-for="value in reason3" v-bind:key = value>{{value}}</span>
      </div>
    </div>

    <div class="control column is-6 is-offset-3">
      <p>次要原因</p>
      <div class="notification is-info" >
        <span style="white-space: pre-wrap" v-for="value in reason4" v-bind:key = value>{{value}}</span>
      </div>
    </div>

    <div class="control column is-6 is-offset-3">
      <p>整改措施</p>
      <div class="notification is-warning" >
        <span style="white-space: pre-wrap" v-for="value in dealway0" v-bind:key = value>{{value}}</span>
      </div>
    </div>

    <div class="control column is-6 is-offset-3">
      <p>防范措施</p>
      <div class="notification is-warning" >
        <span style="white-space: pre-wrap" v-for="value in dealway1" v-bind:key = value>{{value}}</span>
      </div>
    </div>

    <div class="control column is-6 is-offset-3">
      <p>防范整改措施</p>
      <div class="notification is-warning" >
        <span style="white-space: pre-wrap" v-for="value in dealway2" v-bind:key = value>{{value}}</span>
      </div>
    </div>

  </div>
</template>

<script>
export default {
name: "extractor",
  data(){
    return{
      text:'',
      title:'',
      story:'',
      reason0:'',
      reason1:'',
      reason2:'',
      reason3:'',
      reason4:'',
      dealway0:'',
      dealway1:'',
      dealway2:'',
    }
  },
  methods:{

  },
  watch:{
    text(){
      let title_pattern = /^(\s*)《.*?》\s/g
      this.title = this.text.match(title_pattern)

      let story_pattern = /(?<=((.*)事故经过(\n)*))(.*\n)*?\n/g
      this.story = this.text.match(story_pattern)

      let reason0_pattern = /(?<=(((.*)事故原因(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.reason0 = this.text.match(reason0_pattern)

      let reason1_pattern = /(?<=(((.*)直接原因(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.reason1 = this.text.match(reason1_pattern)

      let reason2_pattern = /(?<=(((.*)间接原因(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.reason2 = this.text.match(reason2_pattern)

      let reason3_pattern = /(?<=(((.*)主要原因(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.reason3 = this.text.match(reason3_pattern)

      let reason4_pattern = /(?<=(((.*)次要原因(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.reason4 = this.text.match(reason4_pattern)

      let dealway0_pattern = /(?<=(((.*)整改措施(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.dealway0 = this.text.match(dealway0_pattern)

      let dealway1_pattern = /(?<=(((.*)防范措施(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.dealway1 = this.text.match(dealway1_pattern)

      let dealway2_pattern = /(?<=(((.*)防范整改措施(\s)*)))((.*)([1-9][.．])(.*)(\n)+)*/g
      this.dealway2 = this.text.match(dealway2_pattern)
    }
  }
}
</script>

<style scoped>

</style>