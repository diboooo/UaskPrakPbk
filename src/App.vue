<template>
  <q-layout view="lHh Lpr fFf">
    <q-header elevated class="bg-gradient text-white">
      <q-toolbar>
        <q-btn flat round dense icon="menu" class="text-white" @click="$refs.leftDrawer.open()" />
        <q-toolbar-title class="text-white">
          Weather Dashboard
        </q-toolbar-title>
        <q-space />
      </q-toolbar>
    </q-header>

    <q-drawer ref="leftDrawer" show-if-above bordered content-class="drawer-content">
      <q-list>
        <q-item clickable v-ripple to="/Tugas1">
          <q-item-section>  
            <q-item-label>Tugas 1</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/Tugas2">
          <q-item-section>
            <q-item-label>Tugas 2</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/Tugas3">
          <q-item-section>
            <q-item-label>Tugas 3</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/Tugas4">
          <q-item-section>
            <q-item-label>Tugas 4</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/Tugas5">
          <q-item-section>
            <q-item-label>Tugas 5</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/Tugas6">
          <q-item-section>
            <q-item-label>Tugas 6</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple to="/Tugas7">
          <q-item-section>
            <q-item-label>Tugas 7</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style scoped>

body {
  font-family: 'Poppins', 'Arial', sans-serif;
  background-color: #f5f5f5;
  margin: 0;
}

.q-layout {
  background-color: #f5f5f5;
}

.q-header {
  background-color: transparent;
  color: #fff;
  padding: 10px;
  border-bottom: none;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

.bg-gradient {
  background: linear-gradient(to right, #42a5f5, #1565c0);
}

.text-white {
  color: #fff;
}

.q-toolbar {
  padding: 0 16px;
}

.q-toolbar-title {
  font-size: 1.8em;
  font-weight: bold;
  color: #fff;
}

.q-btn-dropdown {
  display: none; 
}

.drawer-content {
  background-color: #333333;
  color: #fff;
}

.drawer-content .q-item {
  padding: 10px;
  border-bottom: 1px solid #444444;
}

.drawer-content .q-item:last-child {
  border-bottom: none;
}

.drawer-content .q-item:hover {
  background-color: #444444;
}

.drawer-content .q-item-label {
  font-size: 1.2em;
  font-weight: bold;
  color: #fff;
}

.drawer-content .q-item-label a {
  color: #fff;
  text-decoration: none;
}

.drawer-content .q-item-label a:hover {
  color: #fff;
  text-decoration: underline;
}
</style>
