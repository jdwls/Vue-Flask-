<template>
    <div>
        <!-- <div v-for='(index) in $store.state.DirsFileList' :key="index ">
            <div class="data">
                <span>{{index.data }}</span>
                <downloadFlie :down="index.data"></downloadFlie>
                <dropFiles :dropFiles="index.data"> </dropFiles>
                <openDir v-if="index.FileType=='文件夹'" :openDir="index.data"></openDir>
                <ViewButton v-if="index.FileType=='查看文件'" :ViewButtonOfficEword="index.data"> </ViewButton>
            </div>
        </div> -->
        <el-table :data="$store.state.DirsFileList" style="width: 46%" border height="600" :cell-style="{ 'textAlign': 'center' }" :header-cell-style="{ 'text-align': 'center' }" class="juz">
            <el-table-column prop="data" label="文件名" width="360" />
            <el-table-column label="下载" width="120">
                <template #default="scope">
                    <downloadFlie :down="scope.row.data"></downloadFlie>
                </template>
            </el-table-column>
            <el-table-column label="删除" width="120">
                <template #default="scope">
                    <dropFiles :dropFiles="scope.row.data"> </dropFiles>
                </template>
            </el-table-column>
            <el-table-column label="打开文件" width="120">
                <template #default="scope">
                    <openDir v-if="scope.row.FileType == '文件夹'" :openDir="scope.row.data"></openDir>
                </template>
            </el-table-column>
            <el-table-column label="查看文件" width="120">
                <template #default="scope">
                    <ViewButton v-if="scope.row.FileType == '查看文件'" :ViewButtonOfficEword="scope.row.data">1  </ViewButton>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
// import axios from 'axios';
import downloadFlie from '@/components/downloadFlie.vue'
import dropFiles from '@/components/dropFiles.vue'
import openDir from '@/components/openDir.vue'
import ViewButton from '@/components/ViewButton.vue'

export default {
    name: "DirsFileList",
    components: {
        downloadFlie, dropFiles, openDir, ViewButton
    },
    mounted() {
        this.$store.dispatch('DirsFileList')
        this.$store.dispatch('openDirs')

    },
    methods: {
    }
}
</script>
<style scoped>
.data {
    display: flex
}
.juz{
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>