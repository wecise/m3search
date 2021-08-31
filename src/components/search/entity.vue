<template>
    <div class="container">
        <div>
            <el-button type="text" icon="el-icon-warning"> {{dt.title}}</el-button>
        </div>   
        <div style="display:flex;flex-flow: wrap;" class="animated fadeIn">
            <el-button type="default" class="btn-entity" v-for="(item,index) in dt.rows" :key="index">
                <el-image style="width:64px;margin:5px;" :src="item | pickIcon"></el-image>
                <div>
                    <p><span>名称：</span>{{item.name}}</p>
                    <p><span>ID：</span>{{item.id}}</p>
                    <p><span>所属类：</span>{{item.class}}</p>
                    <p><span>创建时间：</span>{{moment(item.vtime).format("YYYY-MM-DD hh:mm:ss")}}</p>
                </div>
            </el-button>
        </div>
    </div>
</template>
<script>
    import _ from 'lodash';

    export default {
        props:{
            dt: Object
        },
        data(){
            return {
                
            }
        },
        filters: {
            pickIcon(item){
                try{
                    let ftype = _.last(item.class.split("/"));
                    return `/static/assets/images/entity/png/${ftype}.png`;
                }
                catch(error){
                    return `/static/assets/images/entity/png/matrix.png`;
                }
            }
        }
    }
</script>

<style scoped>
    .container{
        padding: 20px;
        background: #f2f2f2;
    }
    .btn-entity{
        max-width: 20em;
        width: 20em;
        height:auto;
        border-radius: 10px!important;
        margin: 5px;
        border: unset;
        box-shadow: 0 0px 5px 0 rgba(0, 0, 0, 0.05);
    }
    .btn-entity p{
        text-align: left;
    }
    .btn-entity p>span{
        color:#888888;
    }
</style>
