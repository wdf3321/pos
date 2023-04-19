<template >
<q-page id="setting_commodity" :padding="padding">
  <div class="container ">
    <div class="row ">
      <div class="col-12">
        <!-- commodity form -->
        <q-table
          class="table"
          :rows="commodity"
          :columns="columns"
          row-key="_id"
          :filter="filter"
          :rows-per-page-options="[5, 10, 15, 0]"
        >
          <template v-slot:top-left>
            <div class="col ">
              <h5>商品設定</h5>
              <q-btn
                class="add_btn"
                icon="add"
                color="primary"
                style="font-size: 20px;"
                @click="openAddDialog"
                label="新增商品"
              />
            </div>

          </template>
          <template v-slot:top-right>

            <q-input
              debounce="300"
              v-model="filter"
              placeholder="Search"
            >
              <template v-slot:append>
                <q-icon name="search" />
              </template>
            </q-input>
          </template>
          <template v-slot:body-cell-post="props">
            <q-td class="text-center">
              <q-toggle v-model="props.row.post" color="accent" />
            </q-td>
          </template>
          <template v-slot:body-cell-edit="props">
            <q-td class="text-center q-gutter-sm">
              <q-btn
                icon="edit"
                color="info"
                fab-mini
                unelevated
                size="sm"
                @click="openEditDialog(props.row._id)"
              />
              <q-btn
                icon="delete"
                color="red"
                fab-mini
                unelevated
                @click="deleteCommodity(props.row._id)"
              />
            </q-td>
          </template>
        </q-table>
      </div>
    </div>
  </div>

  <!-- addDialog -->
  <div>
    <q-dialog v-model="showAddDialog" persistent>
      <q-card class="q-pa-md">
        <q-card-section>
          <div class="text-h6">
            {{ dialogTitle }}
          </div>
        </q-card-section>
        <q-card-section>
          <q-form @submit="savecommodityForm" class="q-gutter-md">
            <q-input
              v-model="commodityForm.name"
              label="商品名稱"
              filled
              lazy-rules
              :rules="[val => val.length > 0 || '請輸入商品名稱']"
            />
            <q-select
              v-model="commodityForm.types1"
              label="配菜1"
              filled
              lazy-rules
              :rules="[val => val.length > 0 || '請選擇商品配菜']"
            />
            <q-select
              v-model="commodityForm.types2"
              label="配菜2"
              filled
              lazy-rules
              :rules="[val => val.length > 0 || '請選擇商品配菜']"
            />
            <q-select
              v-model="commodityForm.types3"
              label="配菜3"
              filled
              lazy-rules
              :rules="[val => val.length > 0 || '請選擇商品配菜']"
            />
            <q-select
              v-model="commodityForm.types4"
              label="配菜4"
              filled
              lazy-rules
              :rules="[val => val.length > 0 || '請選擇商品配菜']"
            />
            <q-select
              v-model="commodityForm.types5"
              label="配菜5"
              filled
              lazy-rules
              :rules="[val => val.length > 0 || '請選擇商品配菜']"
            />
            <q-input
              v-model="commodityForm.price"
              label="價格"
              filled
              lazy-rules
              :rules="[val => val.length > 0 || '請設定商品單價']"
            />
            <q-toggle
              v-model="commodityForm.post"
              label="上架"
              color="primary"
            />
            <q-btn
              type="submit"
              color="primary"
              label="儲存"
            />
            <q-btn
              type="submit"
              color="red"
              label="取消"
              @click="showAddDialog = false"
            />
          </q-form>
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>

</q-page>

</template>
<script setup>
import { ref, reactive } from 'vue'
const showAddDialog = ref(false)
const dialogTitle = ref('新增商品')
const commodityForm = reactive({
  name: '',
  types1: '',
  types2: '',
  types3: '',
  types4: '',
  types5: '',
  price: '',
  post: true
})

const openAddDialog = () => {
  showAddDialog.value = true
}
const filter = ref('')
const columns = [

  {
    name: 'name',
    label: '商品名稱',
    field: 'name',
    align: 'center',
    sortable: true
  },
  {
    name: 'types',
    label: '配菜',
    field: 'types',
    align: 'center',
    sortable: true
    // format: (val) => val.join(' ')
  },
  {
    name: 'post',
    label: '上架',
    field: (row) => row.post,
    align: 'center',
    sortable: true
  },
  {
    name: 'price',
    label: '價格',
    field: (row) => row.price,
    align: 'center',
    sortable: true
  },
  {
    name: 'edit',
    label: '編輯/刪除',
    field: (row) => row.edit,
    align: 'center'
  }
]
const commodity = reactive([
  {
    name: '招牌便當',
    types: '豆干、玉米、番茄梅子',
    price: '100',
    post: true

  },
  {
    name: '雞腿便當',
    types: '豆干、玉米、番茄梅子',
    price: '100',
    post: true
  },
  {
    name: '雞胸便當',
    types: '豆干、玉米、番茄梅子',
    price: '100',
    post: true

  },
  {
    name: '滷牛便當',
    types: '豆干、玉米、番茄梅子',
    price: '100',
    post: true

  }
])

</script>
