<template>
    <div>
        <div class="new-collections">
            <table>
                <tbody class="base">
                <tr>
                    <td class="setting-title setting-verticle">赞赏功能</td>
                    <td class="radio">
                        <div class="col-6"><input type="radio" name="push" value="true" checked><span>开启</span></div>
                        <div class="col-6"><input type="radio" name="push" value="false"><span>关闭</span></div>
                    </td>
                </tr>
                <tr>
                    <td class="setting-title pull-left setting-input">赞赏描述</td>
                    <td><textarea placeholder="填写描述"></textarea></td>
                </tr>
                </tbody>
            </table>
            <div class="btn btn-success create">保存</div>
        </div>
    </div>
    </div>
</template>

<script>
</script>

<style scoped>
    .new-collections {
        width: 100%;
        margin: 0 auto;
    }
    .new-collections table {
        width: 100%;
        border-collapse: separate;
        border-spacing: 5px;
        border-color: grey;
    }
    .new-collections td{
        padding: 16px 0;
        font-size: 15px;
    }
    .new-collections .base textarea {
        width: 100%;
        height: 100px;
        margin-bottom: 10px;
        padding: 10px 15px;
        font-size: 15px;
        border: 1px solid #c8c8c8;
        border-radius: 4px;
        background-color: hsla(0,0%,71%,.1);
        display: block;
        resize: none;
        outline-style: none;
    }
    .new-collections .base .setting-title {
        font-size: 15px;
        color: #969696;
    }
    .new-collections .base .setting-verticle {
        vertical-align: bottom;
    }
    .new-collections .base .radio{
        display: flex;
    }
    .new-collections .create{
        margin: 20px 0 50px;
        border-radius: 20px;
        padding: 8px 22px;
        font-size: 16px;
        font-weight: 400;
        line-height: normal;
    }
    .btn-success {
        border-radius: 40px;
        color: #fff;
        background-color: #42c02e;
        border-color: #42c02e;
    }
    .new-collections .create:hover{
        background-color: #42c02e;
        opacity: .8;
    }
</style>