<template>
    <div>
        <el-menu style="width:200px;min-height:calc(100vh - 50px);" default-active="2" class="el-menu-vertical-demo">
            <el-sub-menu index="1">
                <template #title>
                    <el-icon>
                        <location />
                    </el-icon>
                    <span>Navigator One</span>
                </template>
                <el-menu-item index="1-3">item three</el-menu-item>
            </el-sub-menu>
            <el-menu-item index="2">
                <el-icon>
                    <icon-menu />
                </el-icon>
                <span>Navigator Two</span>
            </el-menu-item>
            <el-menu-item index="3">
                <el-icon>
                    <setting />
                </el-icon>
                <span>Navigator Four</span>
            </el-menu-item>
        </el-menu>
    </div>
</template>

<style scoped>
</style>

<script>
import { Location, Document, Menu as IconMenu, Setting, } from '@element-plus/icons'
import { ArrowDown } from "@element-plus/icons";
export default {
    name: "Aside",
    components: {
        Location, Document, Setting, IconMenu, ArrowDown
    }
}
</script>