<template>
  <div id="app">
    <app-header></app-header>
    <app-input></app-input>
    <app-list></app-list>
    <app-footer></app-footer>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader';
import AppInput from './components/AppInput';
import AppList from './components/AppList';
import AppFooter from './components/AppFooter';

export default {
  name: 'app',
  components:{
    'app-header':AppHeader,
    'app-input':AppInput,
    'app-list':AppList,
    'app-footer':AppFooter
  }
}
</script>

<style>
* {box-sizing: border-box;}
</style>
