<template>
  <div style="background-color: #FFF">
    <div class="flex dao-item justify-between align-center">
      <div class="flex">
        <el-image :src="Tools.imgURL(daoInfo.avatar)" class="avatar"></el-image>
        <div class="right-panel">
          <div class="name">{{ daoInfo.name }}</div>
          <div class="normal">{{ daoInfo.contract_address }}</div>
          <!--          <div class="normal">Creation Time:{{ daoInfo.create_time }}</div>-->
          <div class="flex normal">
            <div class="flex">
              <div>Approved:</div>
              <div class="value">{{ daoInfo.approved }}</div>
            </div>
            <div class="flex" style="margin-left: 0.83rem;">
              <div>Rejected:</div>
              <div class="value">{{ daoInfo.rejected }}</div>
            </div>
            <div class="flex" style="margin-left: 0.83rem;">
              <div>Pending:</div>
              <div class="value">{{ daoInfo.pending }}</div>
            </div>
          </div>
        </div>
      </div>
      <div class="flex">
        <el-button color="#EEEEEE" class="edit-btn" @click="emit('edit',daoInfo.contract_address)">Editor</el-button>
        <el-button color="#6E3FF5" class="add-btn" @click="emit('add',daoInfo.contract_address)">
          <img class="add-btn-icon"
               :src="dapp_add2"/>
          Add
        </el-button>
      </div>
    </div>
  </div>

</template>

<script setup>
import {toRef} from "vue";
import dapp_add2 from '@/assets/img/dapp_add2_2x.png';

import Tools from '@/utils/tools';
import dappavatar from '@/assets/img/dapp_dao_tx_2x.png';

const props = defineProps({
  daoInfo: {
    type: Object,
    default: {
      avatar: dappavatar,
      name: '',
      owner: '',
      contract_address: ''
    }
  }
})
const daoInfo = toRef(props, 'daoInfo');
const emit = defineEmits(['edit', 'add'])

</script>

<style lang="scss" scoped>
$font-family: Tomorrow, sans-serif;
.dao-item {
  margin: 0 10rem;
  padding: 1.67em 0;

  .avatar {
    width: 4.17rem;
    height: 4.17rem;
    border-radius: 100rem;
    background: #F5F5F5;
  }

  .right-panel {
    display: flex;
    flex-direction: column;
    margin-left: 0.83rem;

    .name {
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;

      width: 5rem;
      height: 1.17rem;
      font-size: 0.83rem;
      font-family: $font-family;
      font-weight: 500;
      color: #000000;
      line-height: 1.17rem;
    }

    .normal {
      margin-top: 0.17rem;
      height: 0.71rem;
      font-size: 0.5rem;
      font-family: $font-family;
      font-weight: 500;
      color: #999999;
      line-height: 0.71rem;

      .value {
        margin-left: 0.17rem;
        height: 0.71rem;
        font-size: 0.5rem;
        font-family: $font-family;
        font-weight: 500;
        color: #000;
      }
    }
  }
}

.edit-btn {
  width: 3.33rem;
  height: 1.67rem;
  background: #EEEEEE;
  border-radius: 0.33rem;

  span {
    width: 1.92rem;
    height: 0.92rem;
    font-size: 0.67rem;

    font-weight: 500;
    color: #000000;
    line-height: 0.92rem;
  }
}

.add-btn {
  width: 3.33rem;
  height: 1.67rem;
  background: #6E3FF5;
  border-radius: 0.33rem;

  span {
    width: 1.25rem;
    height: 0.92rem;
    font-size: 0.67rem;

    font-weight: 500;
    color: #FFFFFF;
    line-height: 0.92rem;

    .add-btn-icon {
      width: 1rem;
      height: 1rem;
    }
  }
}
</style>
