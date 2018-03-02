<template>
    <div>
        <table class="main">
            <tbody class="account">
            <tr>
                <td class="setting-title top-line">打包下载文章</td>
                <td class="top-line"><a href="javascript:void(0)" class="btn btn-hollow">下载所有文章</a></td>
            </tr>
            </tbody>
        </table>
        <div class="delete-account-content">
            <a class="show-button" @click="showContent = true">
            删除帐号 <i class="fa fa-angle-down"></i></a>
            <transition :duration="200" name="fade">
            <div class="content" v-if="showContent">
                <h4>永久删除帐号</h4>
                <ul>
                    <li>如果你不小心创建出了多余的帐号，或在绑定帐号的时候提示帐号被占用，你可以在<a href="/p/eea64a29cf9d">简书帐号绑定解绑相关问题汇总</a>中获得相关帮助。</li>
                    <li>如果你对简书上的某些内容、功能或社区规则不满意，你可以在<a href="/help">帮助与反馈页</a>向我们提出。</li>
                    <li>删除帐号前，请确保已经没有任何公开或私密文章，且钱包中全部余额已清零。</li>
                    <li>删除帐号是不可逆的操作，删除后将无法恢复。</li>
                </ul>
                <a class="btn btn-hollow" @click="showContent = false">保留我的帐号</a> <a class="btn btn-delete">删除帐号</a>
            </div>
            </transition>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'settmisc',
        data() {
            return {
                showContent:false
            }
        }
    }
</script>

<style scoped>
    .fade-enter-active,.fade-leave-active {
        opacity: 1;
        transition: .3s;
        -webkit-transition: .3s
    }
    .fade-enter,.fade-leave-to {
        opacity: 0;
        transform: translate3d(0,-5%,0);
        -webkit-transform: translate3d(0,-5%,0);
        transition: .3s;
        -webkit-transition: .3s
    }
    .main .setting-title {
        font-size: 15px;
        color: #969696;
    }

    .main .top-line {
        padding-top: 0;
    }

    .main td {
        padding: 20px 0;
    }

    .btn-hollow {
        border: 1px solid rgba(59, 194, 29, .7);
        color: #42c02e !important;
        margin-left: 20px;
        box-shadow: none;
    }
    .btn-delete {
        border: 1px solid rgba(236,97,73,.7);
        color: #ea6f5a!important;
        margin-left: 20px;
    }
    .btn-delete, .btn-hollow {
        padding: 4px 12px;
        font-size: 12px;
        font-weight: 400;
        line-height: normal;
        border-radius: 40px;
        background: none;
    }
    .delete-account-content .show-button {
        margin-bottom: 10px;
        font-size: 15px;
        color: #969696!important;
        cursor: pointer;
    }
    .delete-account-content .content h4 {
        margin-bottom: 25px;
        font-size: 18px;
        color: #969696;
    }
    .delete-account-content .content ul{
        list-style: inherit;
        margin-bottom: 25px;
        padding-left: 20px;
        font-size: 14px;
    }
    .delete-account-content .content ul li{
       margin-bottom: 15px;
        line-height: 20px;
        display: list-item;
        text-align: -webkit-match-parent;
        color: #333333;
    }
    .delete-account-content .content ul li a{
       color: #3194d0!important;
    }
</style>