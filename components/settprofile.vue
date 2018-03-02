<template>
    <div>
        <div class="new-collections">
                <table>
                    <tbody class="base">
                    <tr>
                        <td class="setting-title setting-verticle">性别</td>
                        <td class="radio">
                            <div class="col-3"><input type="radio" name="push" value="true" checked><span>男</span></div>
                            <div class="col-3"><input type="radio" name="push" value="false"><span>女</span></div>
                            <div class="col-3"><input type="radio" name="push" value="false"><span>保密</span></div>
                        </td>
                    </tr>
                    <tr>
                        <td class="setting-title pull-left setting-input">个人简介</td>
                        <td><textarea placeholder="填写描述"></textarea></td>
                    </tr>
                    <tr>
                        <td class="setting-title">个人网站</td>
                        <td class="web-add">
                            <input type="text" name="nick-name" placeholder="http://你的网址">
                            <span>填写后会在个人主页显示图标</span>
                        </td>
                    </tr>
                    <tr>
                        <td class="setting-title pull-left setting-input">微信二维码</td>
                        <td>
                            <a class="btn btn-hollow"><input unselectable="on" type="file"
                                                             class="hide">
                                更换图片
                            </a>
                            <span class="add-weixin">上传后会在个人主页显示图标</span>
                        </td>
                    </tr>
                    <tr>
                        <td class="setting-title setting-input pull-left">社交帐号</td>
                        <td class="social-bind">
                            <p>你可以通过绑定的社交帐号登录简书。出于安全因素, 你最初用来创建账户的社交帐号不能移除。</p>
                            <p>如果帐号被占用，你可以在<a href="javascript:void(0)">简书帐号绑定解绑相关问题汇总</a>
                                中获得相关帮助。</p>
                            <ul class="social-bind-list">
                                <li><div class="bind-name"><i class="fa fa-weibo"></i> <a href="javascript:void(0)">绑定微博<i class="fa fa-angle-right"></i></a></div></li>
                                <li><div class="bind-name"><i class="fa fa-weixin"></i> <a href="javascript:void(0)">绑定微信<i class="fa fa-angle-right"></i></a></div></li>
                                <li><div class="bind-name"><i class="fa fa-qq"></i><a href="javascript:void(0)">绑定QQ<i class="fa fa-angle-right"></i></a></div></li>
                                <li><div class="bind-name"><i class="fa fa-google"></i> <a href="javascript:void(0)">绑定谷歌<i class="fa fa-angle-right"></i></a></div></li>
                            </ul>
                        </td>
                    </tr>
                    </tbody>
                </table>
                <div class="btn btn-success create">创建专题</div>
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
    .new-collections .base .btn-hollow {
        font-size: 14px;
        color: #42c02e;
    }
    .new-collections .base .btn-hollow {
        border: 1px solid rgba(59,194,29,.7);
        color: #42c02e!important;
    }
    .btn-hollow {
        padding: 4px 12px;
        font-size: 12px;
        font-weight: 400;
        line-height: normal;
        border-radius: 40px;
        background: none;
    }
    .new-collections .hide {
        position: absolute;
        display: block!important;
        width: 82px;
        opacity: 0;
    }
    .btn {
        display: inline-block;
        margin-bottom: 0;
        font-weight: 400;
        text-align: center;
        vertical-align: middle;
        -ms-touch-action: manipulation;
        touch-action: manipulation;
        cursor: pointer;
        border: 1px solid transparent;
        white-space: nowrap;
        padding: 6px 12px;
        font-size: 14px;
        line-height: 1.42857;
        border-radius: 15px;
    }
    .btn:hover{
        background: rgba(59,194,29,.2);
    }
    .new-collections .base input {
        padding: 10px 15px;
        font-size: 15px;
        border: 1px solid #c8c8c8;
        border-radius: 4px;
        background-color: hsla(0,0%,71%,.1);
    }
    .new-collections .base .web-add input{
         width: 100%;
        margin-top: 20px;
     }
    .new-collections .base .web-add span{
        float: right;
        color: #969696;
        font-size: 13px;
        margin-top: 10px;
    }
    .new-collections .base .add-weixin{
        float: right;
        font-size: 13px;
        color: #969696;
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
    .new-collections .social-bind p{
          color: #969696;
          font-size: 13px;
      }
    .new-collections .social-bind p a{
        color: #3194d0!important;
        font-size: 13px;
    }
    .new-collections .social-bind-list {
        margin: 0;
        list-style: none;
    }
    .new-collections .social-bind-list li{
        border-bottom: 1px solid #f0f0f0;
        line-height: 50px;
    }
    .new-collections .social-bind-list li i{
        width: 30px;
        font-size: 20px;
        vertical-align: middle;
        display: inline-block;
    }
    .fa-weibo{
        color: #ea6f5a;
    }
    .fa-weixin{
        color: #42c02e;
    }
    .fa-qq{
        color: #3194d0;
    }
    .fa-google{
        color: #ec6119;
    }
    .fa-angle-right{
        font-size: 13px;
        color: #969696;
        margin-left: 10px;
    }
</style>