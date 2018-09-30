<template>
  <div id="app">
    <AppStart/>
  </div>
</template>

<script>
import AppStart from './components/AppStart'

export default {
  name: 'App',
  components: {
    AppStart
  }
}
</script>

<style>
	#app{
		position:relative;
		top:20px;
	}
</style>
