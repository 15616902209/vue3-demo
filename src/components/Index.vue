
<template>

    <el-menu default-active="1-4-1" class="el-menu-vertical-demo sachzhong-sidebar" @open="handleOpen" @close="handleClose"
             :collapse="isCollapse" >
      <div>
        <el-button v-show="isCollapse===true" icon="el-icon-s-unfold" @click="openMenu()" circle></el-button>
        <el-button  v-show="isCollapse===false"  icon="el-icon-menu" @click="closeMenu()" circle></el-button>
      </div>
      <el-divider></el-divider>
      <el-submenu index="1">
        <template #title>
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <template #title>分组一</template>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <template #title>选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <template #title>导航二</template>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <template #title>导航三</template>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <template #title>导航四</template>
      </el-menu-item>
    </el-menu>

</template>

<script>
export default {
  data() {
    return {
      isCollapse: true,
    };
  },
  created() {
  },
  methods: {
    openMenu(){
      this.isCollapse =false;
    },
    closeMenu(){
      this.isCollapse =true;
    },
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
  }
}
</script>

<style>

.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 200px;
  min-height: 400px;
}

.sachzhong-sidebar{
  position: fixed;
  left: 0px;
  top: 100px;
  border:1px solid;
  border-radius: 2px;
  box-shadow: 10px 10px 10px rgba(14,23,32,1);
}
</style>
