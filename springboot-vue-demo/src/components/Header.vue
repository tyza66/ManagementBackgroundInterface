<template>
    <div style="height:50px;line-height:50px;border-bottom:1px solid #ccc;display:flex;">
        <div style="width:200px;margin-left:30px;font-weight:bold;color:#559EFF;">后台管理</div>
        <div style="flex:1;"></div>
        <div style="width:110px; margin-top:8px;margin-right:25px;">
            <el-dropdown>
                <el-button type="primary">
                    洮羱芝闇<el-icon class="el-icon--right">
                        <arrow-down />
                    </el-icon>
                </el-button>
                <template #dropdown>
                    <el-dropdown-menu>
                        <el-dropdown-item>个人信息</el-dropdown-item>
                        <el-dropdown-item>退出系统</el-dropdown-item>
                    </el-dropdown-menu>
                </template>
            </el-dropdown>
        </div>
    </div>
</template>

<style scoped>
</style>

<script>
import { Location, Document, Menu as IconMenu, Setting, } from '@element-plus/icons'
import { ArrowDown } from "@element-plus/icons";
export default {
    name: "Header",
    components: {
        Location, Document, Setting, IconMenu, ArrowDown
    }
}
</script>