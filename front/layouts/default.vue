<template>
  <v-app>
    <nav>
      <v-toolbar dark color="green">
        <v-toolbar-title>
          <nuxt-link to="/">Vue-SNS</nuxt-link>
        </v-toolbar-title>
        <v-spacer />
        <v-toolbar-items>
          <v-form @submit.prevent="onSearchHashtag">
            <div :style="{ display: 'flex', height: '100%', alignItems: 'center' }">
              <v-text-field
                  v-model="hashtag"
                  label="검색"
                  hide-details
                  prepend-icon="mdi-magnify"
              />
            </div>
          </v-form>
          <v-btn text nuxt to="/profile" :style="{display:'flex', alignItems:'center'}">
            <div>프로필</div>
          </v-btn>
          <v-btn text nuxt to="/signup" :style="{display:'flex', alignItems:'center'}">
            <div>회원가입</div>
          </v-btn>
        </v-toolbar-items>
      </v-toolbar>
    </nav>
    <v-row no-gutters><!--no-gutters : 세로 줄 간 패딩 없애기-->
      <v-col cols="12" md="4">
        <login-form></login-form>
      </v-col>
      <v-col cols="12" md="8">
        <nuxt></nuxt><!--라우터 뷰 역할-->
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
import LoginForm from '~/components/LoginForm';

export default {
  components: {
    LoginForm,
  },
  data() {
    return {
      hashtag: '',
    };
  },
  methods: {
    onSearchHashtag() {
      this.$router.push({
        path: `/hashtag/${encodeURIComponent(this.hashtag)}`,
      });
      this.hashtag = '';
    },
  },
  head() {
    return {
      title: 'vue-sns',
    };
  },
};
</script>

<style scoped>
a {
  display: inline-block;
  text-decoration: none;
  color: inherit;
}
</style>
