<!--导航栏组件-->
<template>
    <div id="navi">
        <!--PC端导航栏-->
        <div id="naviPC" v-if="this.$store.state.device !== 'mobile'">
            <!--点击导航项进行路由跳转-->
            <el-menu :default-active="pageSelected" class="el-menu-demo" router mode="horizontal">
                <el-menu-item index="/main/home">主页</el-menu-item>
                <el-menu-item index="/main/album">相册</el-menu-item>
                <el-menu-item index="/main/project">项目</el-menu-item>
                <el-menu-item index="/main/comment">留言</el-menu-item>
                <el-menu-item index="/main/dairy">关于</el-menu-item>
                <div style="height: 60px">
                    <!--音乐播放插件，链接：https://github.com/trsoliu/vue-audio-native-->
                    <vue-audio-native size="default"
                                       :showDownload="false"
                                       :showControls="false"
                                       style="width: 30%; float: right; padding-top: 10vm; height: 100%"
                                       :url="'https://personal-page-tan.oss-cn-beijing.aliyuncs.com/projects/personal_site/music/Pop%5BPSYQUI%5D%20%E5%B0%B1%E5%AF%9D%E5%BE%A1%E7%A4%BC.mp3'"
                    >
                    </vue-audio-native>
                </div>
            </el-menu>
        </div>

        <!--移动端导航栏，换为图标显示，删除音乐播放插件-->
        <div id="naviMobile" v-if="this.$store.state.device === 'mobile'">
            <el-menu :default-active="pageSelected" class="el-menu-demo" router mode="horizontal">
                <el-menu-item index="/main/home" class="mobilenavi"><i class="el-icon-house"></i></el-menu-item>
                <el-menu-item index="/main/album" class="mobilenavi"><i class="el-icon-camera"></i></el-menu-item>
                <el-menu-item index="/main/project" class="mobilenavi"><i class="el-icon-monitor"></i></el-menu-item>
                <el-menu-item index="/main/comment" class="mobilenavi"><i class="el-icon-edit"></i></el-menu-item>
                <el-menu-item index="/main/dairy" class="mobilenavi"><i class="el-icon-user"></i></el-menu-item>
            </el-menu>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Navi",
        computed: {
            /*根据目前所在路由切换导航栏的高亮项*/
            pageSelected: function () {
                if(this.$route.path.replace('/','')==='main/home'){
                    return '/main/home';
                }
                else if(this.$route.path.replace('/','')==='main/album'){
                    return '/main/album'
                }
                else if(this.$route.path.replace('/','')==='main/dairy'){
                    return '/main/dairy'
                }
                else if(this.$route.path.replace('/','')==='main/project'){
                    return '/main/project'
                }
                else{
                    return '/main/comment'
                }
            }
        }
    }
</script>

<style scoped>
    .mobilenavi{
        padding-left: 5%;
        padding-right: 5%;
    }
</style>