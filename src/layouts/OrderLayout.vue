<template>
  <q-layout view="hHh lpR fFf">
    <q-page-container>
      <router-view />
    </q-page-container>
    <q-footer  >
      <div class="oderfooter">
    <q-btn
          color="blue"
          label="點餐"
          icon="restaurant"
          to="/Order"

        />
        <q-btn
          color="blue"
          label="訂單"
          icon="list_alt"
        to="/Document"
        />
        <q-btn
          color="blue"
          label="會員"
          icon="manage_accounts"

        />
        <q-btn
          color="blue"
          label="折扣"
          icon="inventory"

        />
        <q-btn
          color="green"
          label="設定"
          icon="settings"
          to="/Setting"
        />
        <q-btn
          color="red"
         to="/index"
          label="取消訂單"
          icon="logout"

        />
      </div>
    </q-footer>

  </q-layout>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.oderfooter{
  display: flex!important;
  justify-content: space-between!important;
  height: 70px;
  width: 1280px!important;
  margin: 1px!important;
  .q-btn{
    flex: 1;
    width: 213.67px!important;
  height: 70px;
  background: #477DE7;
  color: #FFFFFF;
  font-size: 28px;
  box-shadow: 10px 10px 0px 2px #1564ad;
  // font-size: 42px;

  }
}

</style>
