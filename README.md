## 来由
uView官方的u-swiper轮播图封装得非常漂亮，但可惜不支持自定义，也许是V3编译器不支持$slots缘故，uViewU绝大部分组件都不支持自动识别vuejs的插槽，这里我根据以前修改轮播图的经验对u-swiper进行了修改，让其支持插槽，项目已经测试，现支持**微信小程序、APP(安卓)和H5**。

## 修改说明
>- 增加haveSlot属性，当需要使用插槽时，将其设为ture。如`u-swiper :list="d_list" :haveSlot="true" mode="none">`
>- template部分增加了slot，通过判断haveSlot决定是使用默认的还是自定义的
>- 修改一些属性默认值，减少代码输入量
