<template>
    <div>
        {{aa}}
        <h1 class="father">
            父亲
            <h1 class="son">
                儿子
                <h1 class="sun">
                    孙子
                </h1>
            </h1>
        </h1>
    </div>
</template>
<script>
import mixin from '../mixin'

export default {
    data() {
        return {
            aa:0
        }
    },
    mixins:[mixin],
    mounted() {
        console.log('组件中的挂载');
    },
}
</script>
<style lang="less">
    .father {
        color: red;
        .son {
            color: blue;
        }
    }
</style>