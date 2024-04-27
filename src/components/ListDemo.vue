<template>
    <h1>hekki</h1>
    <p v-for="arr in arrays">{{ arr }}</p>

    <div v-for="item in result">
        <p>
           {{ item.name }} 
           {{ item.age }}
        </p>

        <img :src="item.avatar" alt="avatar" />
    </div>
</template>


<script>
export default {
    data() {    
        return {
            arrays: ['a', 'b', 'c', 'd'],
            result: [
                {
                    name: '张三',
                    age: 18,
                    avatar: 'https://cn.bing.com/images/search?view=detailV2&ccid=q30j%2bOVG&id=E6070001B17962762DEAFA9A7F4D50D6DA9AF9B0&thid=OIP.q30j-OVGku6MskBXpWGlWAAAAA&mediaurl=https%3a%2f%2ftupian.qqw21.com%2farticle%2fUploadPic%2f2020-3%2f20203218142390776.jpg&exph=400&expw=400&q=%e8%87%aa%e7%84%b6%e5%a4%b4%e5%83%8f&simid=607990138049277409&FORM=IRPRST&ck=FC3C94171783BF99F71DF41EF99AAB89&selectedIndex=2&itb=0'
                },
                {
                    name: '李四',
                    age: 20,
                    avatar: 'https://cn.bing.com/images/search?view=detailV2&ccid=%2b%2fA920tk&id=62F5EC57637308EE359157C4B49409ED10E101F4&thid=OIP.-_A920tkCZ62etMcp4gnsQAAAA&mediaurl=https%3a%2f%2ftupian.qqw21.com%2farticle%2fUploadPic%2f2020-3%2f202032322421127909.jpg&exph=400&expw=400&q=%e8%87%aa%e7%84%b6%e5%a4%b4%e5%83%8f&simid=608026958785772254&FORM=IRPRST&ck=C154FA880D74FAEC8A0B99DC576463F5&selectedIndex=3&itb=0'
                },
                {
                    name: '王五',
                    age: 22,
                    avatar: 'https://cn.bing.com/images/search?view=detailV2&ccid=cef7nnIy&id=457EC80FCD5EE9AB67B2A2DC3CD34D8355814898&thid=OIP.cef7nnIyvGQojAfHgmf3hwAAAA&mediaurl=https%3a%2f%2fts1.cn.mm.bing.net%2fth%2fid%2fR-C.71e7fb9e7232bc64288c07c78267f787%3frik%3dmEiBVYNN0zzcog%26riu%3dhttp%253a%252f%252fimg.pconline.com.cn%252fimages%252fupload%252fupc%252ftx%252fwallpaper%252f1305%252f16%252fc4%252f20990657_1368686545115.jpg%26ehk%3dPa%252fePSmCai5e0521TPeplbk94pGQpyx%252bAblA5Y2KCrQ%253d%26risl%3d%26pid%3dImgRaw%26r%3d0&exph=296&expw=474&q=%e8%87%aa%e7%84%b6%e5%a4%b4%e5%83%8f&simid=608026258673920980&FORM=IRPRST&ck=944AF641CD3817301953B4908E6B0B8F&selectedIndex=9&itb=0'
                }
            ]
        }

    }
}
</script>