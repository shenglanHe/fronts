<style lang="less">
    .info{
        padding-top: 20px;
        h3{
            color:#2d8cf0;
            font-size: 16px;
            padding:0px 0px 10px 25px;
            :before{
                position:absolute;
                top:25px;
                left:10px;
                content:'';
                width:5px;
                height:12px;
                background-color:#2d8cf0;
            }
        }
        .ivu-row{
            height:40px;
            line-height: 40px;
            margin-bottom: 8px;
            
            .labelname{
                text-align: right;
                span{
                    padding-right: 10px;
                }
            } 
            input{
                width: 300px;
                height: 32px;
                padding:6px;
                border-radius: 7px;
                border:1px solid #dddee1;
            }
            .ivu-select{
                width: 300px;
            }
            .ivu-checkbox-group{
                display: inline-block;
            }
        }
        
    }
</style>
<template>
<div class="info">
    <div v-for="(formdata, index) in pageData" :key="formdata.pageId">
      <h3><span>{{formdata.pageName}}</span></h3>
      <Form ref="formdata" :model="formdata" :label-width="120">
        <Row>
          <Col v-for="(item,index) in formdata.details" :key="index" :span="24/item.col" class="columnstyle1">
            <template v-if="item.type === 'input'">
                <Form-item :label="item.name" :prop="item.value" :rules="{required: true,message:'not empty',trigger:'blur'}">
                    <i-input v-model="item.value" :placeholder="item.placeholder" ></i-input>
                </Form-item>
            </template>
        </Col>
        </Row>
      </Form> 
    </div>
    <Button type="primary" @click="submit" size="large">Submit</Button>
</div>    
</template>
<script>
    export default {
        data () {
            return { 
               pageData:[{
                    "details": [
                            {
                                "col": "1",
                                "readOnly": "0",
                                "type": "input",
                                "required": "0",
                                "regex": null,
                                "name": "所属社区",
                                "placeholder": "请获取信息",
                                "text": "community",
                                "value": ""
                            },
                            {
                                "col": "2",
                                "readOnly": "0",
                                "type": "input",
                                "required": "1",
                                "regex": null,
                                "name": "身份证号",
                                "placeholder": "请获取信息",
                                "text": "id_num",
                                "value": ""
                            }],
                    "pageId": 14,
                    "pageName": "基本表单1"
                },{
                    "details": [
                            {
                                "col": "2",
                                "readOnly": "0",
                                "type": "input",
                                "required": "1",
                                "regex": null,
                                "name": "姓名",
                                "placeholder": "请获取信息",
                                "text": "id_num",
                                "value": ""
                            }],
                    "pageId": 15,
                    "pageName": "基本表单2"
                }]
            }
        },
        methods: {
            submit () {

                // 在这里可以拿到用户输入的值，通过v-model赋的值
                // 我在这里就直接取值了，这里的麻烦之处就在于可能需要遍历formData来取到对应的值
                // 可以使用数组的find方法 
                for(var i=0;i<this.formData.length;i++){
                    console.log(this.formData[i].val);
                }
            }
        }
    }
</script>
