<template>
    <div class="list">
        <div class="list-box" v-for="o in list" :key="o.auctionId">
            <div class="pic-box">
                <a :href="o.auctionUrl" class="box-img">
                    <span class="empty-bg"></span>
                    <img :src="o.pictUrl">
                </a>
            </div>
            <div class="box-content">
                <div class="content-line">
                    <p>
                        <a :href="o.auctionUrl" v-html="o.title"></a>
                    </p>
                </div>
                <div class="content-line">
                    <span class="fl">{{o.zkPrice}}</span>
                    <span class="fr">月销:{{o.biz30day}}</span>
                </div>
                <div class="content-line">
                    <span class="fl">卖家:{{o.nick}}</span>
                    <span class="fr">
                        <span v-if="o.userType == 1" class="tag tag-tmall"></span>
                    </span>
                </div>
                 <div class="content-line">
                    <span class="fl">店铺:{{o.shopTitle}}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import axios from "axios";


export default {
    data(){
        return {
            list: []
        }
    },
    methods: {
        parseData(datas){
            this.list = datas.data.pageList;
        }
    },
    mounted() {
        let _this = this;
        axios.get('/server/getTaobao')
            .then(function (res) {
                if(res.status == 200){
                    _this.parseData(JSON.parse(res.data));
                }
            }).catch(function (err) {
                console.log(error);
            });
    }
}

</script>

<style lang="scss">

.tag{
        height: 16px;
    width: 16px;
    text-align: center;
    line-height: 16px;
    display: inline-block;
    vertical-align: middle;
    margin-right: 6px;
}
.tag-tmall {
    background-image: url(//img.alicdn.com/tps/TB1XfA2JVXXXXcQXXXXXXXXXXXX-16-16.png);
    background-image: -webkit-image-set(url(//img.alicdn.com/tps/TB1XfA2JVXXXXcQXXXXXXXXXXXX-16-16.png) 1x,url(//img.alicdn.com/tps/TB1xRA6JVXXXXXYXXXXXXXXXXXX-32-32.png) 2x);
    background-image: -ms-image-set(url(//img.alicdn.com/tps/TB1XfA2JVXXXXcQXXXXXXXXXXXX-16-16.png) 1x,url(//img.alicdn.com/tps/TB1xRA6JVXXXXXYXXXXXXXXXXXX-32-32.png) 2x);
    background-image: -o-image-set(url(//img.alicdn.com/tps/TB1XfA2JVXXXXcQXXXXXXXXXXXX-16-16.png) 1x,url(//img.alicdn.com/tps/TB1xRA6JVXXXXXYXXXXXXXXXXXX-32-32.png) 2x);
}

.fl{
    float: left;
}
.fr{
    float: right;
}
a{
    color: #666;
    outline: 0;
    text-decoration: none;
}
.list{
    width: 1200px;
    margin: 20px auto;
    overflow-y: hidden;
}

.list-box{
    float: left;
    position: relative;
    width: 220px;
    height: 410px;
    background: #fff;
    margin-left: 20px;
    margin-top: 20px;
    border: 1px solid #ccc;
    -moz-box-shadow: 0 1px 3px 0 rgba(32,32,64,.04);
    -webkit-box-shadow: 0 1px 3px 0 rgba(32,32,64,.04);
    -ms-box-shadow: 0 1px 3px 0 rgba(32,32,64,.04);
    -o-box-shadow: 0 1px 3px 0 rgba(32,32,64,.04);
    box-shadow: 0 1px 3px 0 rgba(32,32,64,.04);
    -moz-transition: all .2s ease-out;
    -webkit-transition: all .2s ease-out;
    -ms-transition: all .2s ease-out;
    -o-transition: all .2s ease-out;
    transition: all .2s ease-out;
    .pic-box{
        position: relative;
        margin: 1px;
    }
    .box-img{
        display: table-cell;
        vertical-align: middle;
        text-align: center;
        width: 218px;
        height: 218px;
        img{
            max-width: 218px;
            max-height: 218px;
            position: relative;
            opacity: 1;
            border: 0 none;
            width: auto\9;
            height: auto;
            max-width: 100%;
            vertical-align: top;
            -ms-interpolation-mode: bicubic;
            -moz-transition: opacity .3s ease-out;
            -webkit-transition: opacity .3s ease-out;
            -ms-transition: opacity .3s ease-out;
            -o-transition: opacity .3s ease-out;
            transition: opacity .3s ease-out;
        }
    }
    .empty-bg{
        background: url(//img.alicdn.com/tps/TB1Q736LXXXXXXpXFXXXXXXXXXX-32-32.png) 50% 50% no-repeat;
        display: block;
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
    }
    .box-content{
        background: #fff;
        width: 100%;
        height: 107px;
        padding-top: 7px;
    }
    .content-line{
        line-height: 28px;
        padding: 0 10px;
        p{
            line-height: 20px;
    height: 40px;
    overflow: hidden;
        }
        a{
            color: #666;
            font-size: 12px;
        }
    }
}
</style>
