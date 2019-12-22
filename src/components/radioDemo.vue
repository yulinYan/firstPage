<!--
<template>
    <div style="display: flex;align-items: center ">
        <el-checkbox :indeterminate="isIndeterminate" v-model="checkAll" @change="handleCheckAllChange">全选</el-checkbox>
        <div style="margin: 15px 0;">
            <el-checkbox-group v-for="item in 2" :key="item" v-model="checkedCities" @change="handleCheckedCitiesChange">
                <el-checkbox v-for="city in cities" :label="city" :key="city">{{city}}</el-checkbox>
            </el-checkbox-group>
        </div>
    </div>
</template>

<script>
    const cityOptions = ['上海', '北京', '广州', '深圳'];
    export default {
        name: "radioDemo",
        data() {
            return {
                checkAll: false,
                checkedCities: [],
                cities: cityOptions,
                isIndeterminate:false
            };
        },
        methods: {
            handleCheckAllChange(val) {
                this.checkedCities = val ? cityOptions : [];
                this.isIndeterminate = false;
            },
            handleCheckedCitiesChange(value) {
                let checkedCount = value.length;
                this.checkAll = checkedCount === this.cities.length;
                this.isIndeterminate = checkedCount > 0 && checkedCount < this.cities.length;
            }
        }
    }
</script>

<style scoped>

</style>-->
<template >
    <div>
        <el-table
                :data="tableData"
                :span-method="objectSpanMethod"
                 border
                stripe
                style="width: 100%; margin-top: 20px">
            <el-table-column
                    prop="model1"
                    label="模块一"
                    width="180"
                    align="center">
                <template slot-scope="scope">
                    <el-checkbox
                            size="mini"
                            v-for=" (item, index)  in scope.row.model1"
                            :key="index" v-model="item.checked" @change="handleCheckAllChange">{{item.name}}</el-checkbox>
                </template>
            </el-table-column>
            <el-table-column
                    prop="model2"
                    label="模块二"
                    width="180"
                    align="center">
            <template slot-scope="scope">
                <el-checkbox
                        size="mini"
                        v-for=" (item, index)  in scope.row.model2"
                        :key="index" v-model="item.checked" @change="handleCheckAllChange">{{item.name}}</el-checkbox>
            </template>
            </el-table-column>
            <el-table-column
                    prop="model3"
                    label="模块三"
                    align="center">
                <template slot-scope="scope">
                    <el-checkbox
                            size="mini"
                            v-for=" (item, index) in scope.row.model3"
                            :key="index"  @change="handleCheckedCitiesChange">{{item}}</el-checkbox>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
    export default {
        name: "radioDemo",
        data() {
            return {
                tableData: [{
                    model1: [{name:'首页',checked:false}],
                    model2: [{name:'首页',checked:false}],
                    model3: ''
                },{
                    model1: [{name:'我的地盘',checked:false}],
                    model2: [{name:'我的地盘1',checked:false}],
                    model3: ['165']
                }, {
                    model1: [{name:'我的地盘',checked:false}],
                    model2: [{name:'我的地盘2',checked:false}],
                    model3: ['165']
                }, {
                    model1: [{name:'代办',checked:false}],
                    model2: [{name:'我的代办1',checked:false}],
                    model3: ['234','2344','56']
                }, {
                    model1: [{name:'代办',checked:false}],
                    model2:[{name:'我的代办2',checked:false}],
                    model3: ['621']
                }, {
                    model1: [{name:'产品计划',checked:false}],
                    model2: [{name:'产品计划',checked:false}],
                    model3: ['539']
                }, {
                    model1: [{name:'发布',checked:false}],
                    model2: [{name:'发布硬件',checked:false}],
                    model3: ['539']
                }]
            };
        },
        methods: {
            handleCheckAllChange() {
                // eslint-disable-next-line no-console
                console.log(this);
                this.checked = true;
            },
            handleCheckedCitiesChange(value) {
                let checkedCount = value.length;
                this.checkAll = checkedCount === this.cities.length;
                this.isIndeterminate = checkedCount > 0 && checkedCount < this.cities.length;
            },
            objectSpanMethod({  rowIndex, columnIndex }) {
                if (columnIndex === 0 &&(rowIndex===1||rowIndex===3)) {
                        return {
                            rowspan: 2,
                            colspan: 1
                        };

                } else if (columnIndex === 0 &&(rowIndex===2||rowIndex===4)) {
                    return {
                        rowspan: 0,
                        colspan: 0
                    };

                }else {
                    return {
                        rowspan: 1,
                        colspan:1
                    };
                }
            },
            formatText(row, column, cellValue){
             if(cellValue==='我的代办1'){
                 return '<p style="background-color: firebrick">你好</p>'
             }else{
                 return cellValue
             }
            }
        }
    };
</script>
<style scoped>
    .cell{height: 100px !important;overflow: auto !important;}
</style>