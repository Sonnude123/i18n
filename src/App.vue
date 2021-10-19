<template>
	<div id="app">
		<img width=200 src="./assets/hinh-nen.png">
		<h1>{{ 'Demo i18n is so easy' | translate }}</h1>
		<p>{{ $t('content', {'type': 'bananas'}) }}</p>
		<select v-model="selectedLanguage">
			<option v-for="lang in languages" :key="lang" :value="lang">{{lang.long}}</option>
		</select>
		{{selectedLanguage}}
	</div>
</template>

<script>
	import {mapState} from 'vuex';
	import Vue from 'vue';

	export default {
    name: 'app',
		computed: mapState(['languages']),
		created() {
			Vue.i18n.set(this.$store.state.curLanguage.short);
		},
		data() {
			return {
				selectedLanguage: this.$store.state.curLanguage,
			}
		},
		watch: {
			'selectedLanguage': function(newLang) {
				Vue.i18n.set(newLang.short);
				this.$store.commit('setLanguage', newLang.short);
			}
		}
  }
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>