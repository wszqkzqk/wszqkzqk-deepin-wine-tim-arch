# 在arch以及衍生版本上运行deepin-TIM

   用过deepin的都应该知道，deepin的wine-QQ，wine-TIM运行都十分完美，这个便是把deepin打包的TIM容器移植到arch来运行。
   
   TIM，不解释，轻量无广告版的超级QQ。
   
   当然，由于我无法将deepinwine移过来（deepin论坛官方管理员jingle貌似说deepinwine不对外，但是容器好像可以），所以我只好用普通wine替代deepinwine兼容运行。这样也就会存在如下bug：

1.无法视频通话

2.无法记住密码
  
  
  清风博主的wine-qq也有这两个bug（他忽略了视频通话，没写），但是他没有列出断线问题，经我的初步测试，这款deepin-tim-for-arch挂一晚上不掉线还是可以的，但是，有一种情况真的会掉线：网络环境发生变化或者网络质量差到断流。如果发生上述情况，请关闭程序重新运行。Linux下很难找到能够掉线后自动重连的wine-QQ或wine-TIM（除了deepin自家，但是其他发行版不可用），lulinux好像在他的博客分享了一款，但是那毕竟是QQ2013，太旧了，按照腾讯的坑规则，很快就无法登录了。
  
  
  安装输入：
  
  
  
  方法1：
  
  
  
  mkdir wszqkzqk-deepin-wine-tim-arch
  
  cd wszqkzqk-deepin-wine-tim-arch
  
  wget https://raw.githubusercontent.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch/master/PKGBUILD
  
  makepkg -i 
  
  
  
  方法2：
  
  
  
  git clone https://github.com/wszqkzqk/wszqkzqk-deepin-wine-tim-arch
  
  cd wszqkzqk-deepin-wine-tim-arch
  
  makepkg -i
  
  然后直接运行开始菜单中创建的TIM的图标，它会提示安装，点击立即安装即可（我去掉了自带的TIM，替换为了最新版）
  

  如果看不惯字体发虚又懒得配置的，可以看看lulinux大神的博客：https://www.lulinux.com ，里面有一键配置（PS：大神做得辛苦要求捐赠不要喷我。。。）
  
  欢迎大家测试反馈。
