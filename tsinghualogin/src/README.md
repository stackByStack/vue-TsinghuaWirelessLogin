# 1. 目录结构及解释
src/
    App.vue # 单页应用文件（vue为单页式应用，不同页面的转换通过路由跳转实现）
    main.ts # 挂载app
    shims-vue.d.ts # 不知道
    assets/
        logo.png
        css/
            Popout.scss
        image/
            disconnect.png
            icon16-yellow.ico
            icon32.png
            usage_bg.gif
            wireless/
                account.gif
                background.png
                greeting.png
                logo.gif
                notice.png
                phone_account.gif
                popup_bg.png
                popup_greeting.png
                popup_info.gif
                popup_learn.gif
                popup_lib.gif
                popup_mail.gif
                popup_shadow.png
                title.png
    components/
        HelloWorld.vue 
        Popout.vue # popout组件，直接复制粘贴html了，可以修改用户名、连接时间、流量
    router/
        index.ts # 路由控制，就是控制页面显示哪个部分的内容（统一写在views里
    store/
        index.ts # 状态控制，相当于全局统一控制变量，大家可以尝试把popout.vue里的变量改写到这里
    views/
        AboutView.vue
        HomeView.vue
        PopoutView.vue 页面显示
# 2. TODO
1. 进度条的实现可能可以更优雅一些？https://github.com/stackByStack/vue-TsinghuaWirelessLogin/blob/b42522f4e0ef8e06294ea51d710d9ccaaa92dd69/tsinghualogin/src/components/Popout.vue#L26C61-L26C61
2. 连接时间、流量的更新可能不够规范，理论上需要利用computed（vue自动分析计算一个变量的全部依赖项，一旦依赖项改变，重新计算该变量）
