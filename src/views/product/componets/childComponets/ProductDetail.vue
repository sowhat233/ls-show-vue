<template>

    <editor-bar v-model="value"></editor-bar>

</template>

<script>

    import EditorBar from '@/components/wangEnduit/Index';

    export default {
        name: "ProductDetail",
        props: {
            //商品详情
            product_detail: {
                type: String,
                default: ''
            },
        },
        components: {
            EditorBar,
        },
        data() {
            return {
                value: ''
            };
        },
        created() {


        },
        methods: {
            //验证数据
            validate() {

                //判断是否为空
                if (this.value === '') {

                    this.$message.error({
                        'message': '请填写商品详情',
                    });

                    //告诉父组件验证不通过
                    this.$emit('validateFailed');

                }

            },
            //给父组件返回数据
            returnData() {

                let product_detail = {
                    'product_detail': this.value,
                };

                //发送表单的数据
                this.$emit('returnData', product_detail);

            },
        },
        watch: {
            product_detail(value, old_value) {

                this.value = value;
            }
        }
    };
</script>

<style scoped>


</style>