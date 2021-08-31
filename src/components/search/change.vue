<template>
    <div>
        <div>
            <el-button type="text" icon="el-icon-warning"> {{dt.title}}</el-button>
        </div>   
        <div class="animated fadeIn">
            <el-table
                :data="dt.rows"
                stripe
                style="width: 100%">
                <template v-for="(item,index) in dt.columns">
                    <el-table-column
                        :key="index"
                        :prop="item.field"
                        :label="item.title"
                        :width="item.width"
                        :visible="item.visible">
                    </el-table-column>
                </template>
            </el-table>
        </div>
    </div>
</template>
<script>
    export default {
        props:{
            dt: Object
        },
        data(){
            return {
                
            }
        }
    }
</script>
