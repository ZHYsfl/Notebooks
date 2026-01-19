[TOC]

# Note

## 1. 基础语法

变量、枚举类型、联合类型、类型别名、函数、箭头函数、类、接口、组件、组件内变量和函数：

```ts
let num : number = 0 // let不能放到struct里，可以用于声明全局变量
enum ColorSet{ // 声明枚举类型
    white = '1',
    black = '2',
}
let color : ColorSet = ColorSet.white
let luckyNum : number | boolean | string | ColorSet = true // 联合类型
type ID = number // aliases
let userID : ID = 1
function submit(){ // 声明函数
    // 逻辑
}

()=>{ // 箭头函数
    // 逻辑
}

class User{ // 声明类
    build(name : string,age : number,isMale : boolean){
        this.name = name
        this.age = age
        this.isMale = isMale
    }
    name : string = '张三'
    age : number = 20
    isMale : boolean = true
}

const user : User = new User()
luckyNum = User.name

// 接口
interface userType{
    name : string,
    age : number,
    email ? : string, // ? 代表可有可无（可选）
}
let userArray : userType[] = {
    {name:'1',age:2,emial:'3'},
    {name:'2',age:3}
}

@Entry
@Component
struct TestPages{
    
    // 定义数据
   	@State str : string = 'qwen'
    @State age : number = 20
    
    // 内部声明函数，无需function
    submitFun(){
        if(true){
            this.age = 30
            // ...
        }
    }
    
    build(){
        // build中写UI描述，页面信息
    }
}
```

---

## 2. Column

```ts
@Entry
@Component
struct ZHY{
    build(){
        Column(){
            Text("55230121周浩洋")
        }
        .width(200)
        .height(200)
        .backgroundColor(Color.Pink)
        // 边框
        .border({width:2,color:Color.Red})
        .padding(60)
    }
}
```

```ts
@Entry
@Component
struct ColumnTest{
  build() {
    // 列布局
    Column({space:100}){
      Text()
        .width(50)
        .height(50)
        .border({width:10})
      Text()
        .width(50)
        .height(50)
        .border({width:10})
      Text()
        .width(50)
        .height(50)
        .border({width:10})
      Text()
        .width(50)
        .height(50)
        .border({width:10})
    }
    .width('100%')
    .height('100%')
    .border({width:5})

    // 主轴
    .justifyContent(FlexAlign.Center)

    // 侧轴 Horizontal Align
    .alignItems(HorizontalAlign.Start)
  }
}
```

---

## 3. Swiper

```ts
@Entry
@Component
struct SwiperTest {
  build() {
    // 层叠布局
    Swiper(){
      Text('1').width('100%').height('100%').backgroundColor(Color.Red)
      Text('2').width('100%').height('100%').backgroundColor(Color.Blue)
      Text('3').width('100%').height('100%').backgroundColor(Color.Yellow)
        
    }
    .width('100%')
    .height('20%')
    .border({width:5})
    .loop(true)
    .autoPlay(true)
  }
}
```

## 4. Stack

```ts
@Entry
@Component
struct StackTest {
  build() {
    // 层叠布局
    Stack({alignContent:Alignment.TopStart}){
      Text().width(200).height(200).backgroundColor(Color.Red).zIndex(2) //无zIndex默认底层
      Text().width(100).height(100).backgroundColor(Color.Blue).zIndex(3) //无zIndex默认后面的层级高
    }
    .width('100%')
    .height('100%')
    .border({width:5})
  }
}
```

---

## 5. Scroll

```ts
@Entry
@Component
struct ScrollTest {
  build() {
    // 滑动组件
    Scroll(){
     Text().height(2000).width('100%').border({width:2})
    }
    .scrollBarWidth(50)
  }
}
```

## 6. Row

```ts
@Entry
@Component
struct RowTest {
  build() {
    // 行布局
    // 默认侧轴居中
    Row(){
      // RowSplit(){
      //   Text()
      //     .width(50)
      //     .height(50)
      //     .border({width:10})
      //   Text()
      //     .width(50)
      //     .height(50)
      //     .border({width:10})
      //
      //   Text()
      //     .width(50)
      //     .height(50)
      //     .border({width:10})
      //   Text()
      //     .width(50)
      //     .height(50)
      //     .border({width:10})
      // }
      Text()
        .width(50)
        .height(50)
        .border({width:10})
      Blank().backgroundColor(Color.Gray)
      Text()
        .width(50)
        .height(50)
        .border({width:10})
      Blank().backgroundColor(Color.Gray)
      Text()
        .width(50)
        .height(50)
        .border({width:10})
      Blank().backgroundColor(Color.Gray)
      Text()
        .width(50)
        .height(50)
        .border({width:10})

    }
    .width('100%')
    .height('100%')
    .border({width:5})
    // 主轴位置
    // .justifyContent(FlexAlign.Center)
    // .justifyContent(FlexAlign.SpaceBetween)

    // 边框和节点之间距离是节点和节点的1/2
    // .justifyContent(FlexAlign.SpaceAround)

    .justifyContent(FlexAlign.SpaceEvenly)

    // 侧轴 Vertical Align
    .alignItems(VerticalAlign.Top)

  }
}
```

---

## 7. Flex

```ts
@Entry
@Component
struct FlexTest{
  build() {
    Flex({direction:FlexDirection.ColumnReverse,wrap:FlexWrap.Wrap,
    justifyContent:FlexAlign.Start,alignContent:FlexAlign.Start}){
      Text('1').width(50).height(50).border({width:2})
      Text('2').width(50).height(50).border({width:2})
      Text('3').width(50).height(50).border({width:2})
      Text('1').width(50).height(50).border({width:2})
      Text('2').width(50).height(50).border({width:2})
      Text('3').width(50).height(50).border({width:2})
      Text('1').width(50).height(50).border({width:2})
      Text('2').width(50).height(50).border({width:2})
      Text('3').width(50).height(50).border({width:2})
      Text('1').width(50).height(50).border({width:2})
      Text('2').width(50).height(50).border({width:2})
      Text('3').width(50).height(50).border({width:2})
      Text('1').width(50).height(50).border({width:2})
      Text('2').width(50).height(50).border({width:2})
      Text('3').width(50).height(50).border({width:2})
      Text('1').width(50).height(50).border({width:2})
      Text('2').width(50).height(50).border({width:2})
      Text('3').width(50).height(50).border({width:2})
    }
    .width('100%')
    .height('100%')
    .border({width:5})

  }
}
```

---

## 8. Grid

```ts
@Entry
@Component
struct GridTest {
  build() {
    // 行布局
    // 默认侧轴居中
    Grid(){
      // Grid中子元素只能是GridItem
      // GridItem(){ // GridItem中只能有一个根节点
      //   Flex(){
      //     Text()
      //   }
      // }
      GridItem(){Text('1')}.border({width:2})
      GridItem(){Text('2')}.border({width:2})
      GridItem(){Text('3')}.border({width:2})


    }
    .width(300)
    .height(300)
    .border({width:5})
    .columnsTemplate('1fr 1fr 1fr  1fr')
    .rowsTemplate('1fr 1fr 1fr 1fr')
  }
}
```

---

## 9. Tabs

```ts
import {ListTest} from './ListTest'
@Entry
@Component
struct TabsTest{
  build() {
    // tabs导航
    Tabs({barPosition:BarPosition.End}){
      TabContent(){
        //设置导航名称
        ListTest()
      }
      // .tabBar({icon:'',text:''})
      .tabBar('微信')
      TabContent(){
        Search({value:'',placeholder:'请输入'})
        // 搜索按钮
          .searchButton('搜索',{fontSize:20,fontColor:Color.Blue})
          .onSubmit((value : string)=>{
            console.log('jida  onSubmit '+value)
          })
          .onChange((value : string)=>{
            console.log('jida  onChange '+value)
          })

      }
      .tabBar('通讯录')
      TabContent(){
        Text('3')
      }
       .tabBar('发现')
      TabContent(){
        Text('4')
      }
       .tabBar('我')
    }
    .onChange((index:number)=>{
      console.log('jida    '+ index)
    })
    .scrollable(false)
    .barWidth(400)
    .barBackgroundColor(Color.White)
    .vertical(false)
  }
}
```

---

## 10. Text().border

```ts
@Entry
@Component
struct BorderTest {

  build() {
    Text()
      .width(100)
      .height(100)
      // 边框
      .border({
        width: { top: 10, right: 2, bottom: 5, left: 2 },
        color:Color.Blue,
      })
      // 圆角
      // .borderRadius(20)
      .borderRadius({topLeft:50,bottomRight:50})
      // 样式
      .borderStyle(BorderStyle.Dashed)
  }

}
```

---

## 11. @Builder and Button

```ts
import { text } from '@kit.ArkGraphics2D'

@Entry
@Component
struct BuilderTest{

  @State num : number = 0

  //定义builder
  @Builder textBuilder(title : string){
    //UI 逻辑
    Text(title)
  }
  @Builder textBuilder1(){
    //UI 逻辑
    Text('BuilderContent')
  }
  @Builder textBuilder2(){
    //UI 逻辑
    Text('BuilderContent')
  }

  build() {
    Column(){
      // 列布局，相当于最外层盒子
      this.textBuilder('Builder')
      this.textBuilder1()
      this.textBuilder2()

      // 按钮 样式
      Button('按钮')
        .stateStyles({
          focused:{
            .backgroundColor(Color.Red)
            .width(200)
          },
          normal:{
            .backgroundColor(Color.Black)
            .width(50)
          },
          pressed:{
            .backgroundColor(Color.Yellow)
            .width(100)
          }
        })

    }
  }
}
```

----

## 12. @Prop and @Link

@Prop是父组件向子组件单向传送数据用的
@Link是父子组件之间双向传输数据用的

```ts
//DataTest.ets

import {DataTestSon} from './DataTestSon'

@Entry
@Component
struct DataTest{

  @State num : number = 0

  build() {
    // // text组件参数必须为字符串
    // Text(this.num.toString())
    //   .onClick(()=>{
    //     this.num++
    //   })

    Column(){

      Text('parent original value'+this.num.toString())
        .onClick(()=>{
          this.num++
        })

      // 使用子组件并传值 {var:value}
      DataTestSon({count:this.num})
    }


  }
}
```

```ts
// DataTestSon.ets

@Component
export struct DataTestSon{ // 被父组件使用要先导出

  // @Prop count : number

  @Link count : number

  // 子页面
  build() {
    // text组件参数必须为字符串
    Text('child value is:'+this.count.toString())
      .onClick(()=>{
        this.count++
      })
  }
}
```

---

## 13. if else

```ts
@Entry
@Component
struct  IfElseTest{

  @State flag : boolean = true
  @State button_text : string = ""

  GetButtonText(){
    if(this.flag) return "turn to false"
    else return "turn to true"
  }
  build() {

    Column(){
      Button(this.GetButtonText())
        .onClick(()=>{
          this.flag = !this.flag
        })
      // 条件渲染
      if(this.flag){
        Text("i'm true")
      }else{
        Text("i'm false")
      }
    }
  }
}
```

---

## 14. ForEach

```ts
interface arrItem{
  name : string,
  age : number,
}

@Entry
@Component
struct ForEachTest{
  @State arr : number[] = [1,2,3,4]
  @State arr1 : string[] = ['1','2','3','4']
  // 第一步 定义数据源
  @State arr2 : arrItem[] = [
    {name:'1',age:2},
    {name:'3',age:4},
  ]

  build() {
    Column(){
      // ui循环生成函数
      // 数据源，循环函数
      ForEach(
        this.arr2,
        (item:arrItem,index:number)=>{
          // 被循环ui内容
          Text(index.toString()+':我叫'+":"+item.name.toString()+"年龄为:"+item.age.toString())
            .fontSize(40)
        }
      )
    }
  }
}
```

使用ForEach渲染微信界面：

```ts
interface message{
  imgUrl: string | Resource, // Resource是$获取的地址
  name : string,
  messageData : string,
}

@Entry
@Component
struct ListTest{
  @State messageList : message[] = [
    {imgUrl:$rawfile('myown.jpg'),name:'zhouhaoyang',messageData:'[30条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/R.3f505e222d848cf935ae5463ced6b7be?rik=X4jD3uI%2fMiCziA&riu=http%3a%2f%2fi1.hdslb.com%2fbfs%2farchive%2f84201a88b395fa4a547961f2c45d1957e2b25631.jpg&ehk=Aca2Rr8PRcsWGgxPa%2f%2fUHQpk6pWK9FA9KFchTjf0awQ%3d&risl=&pid=ImgRaw&r=0',name:'balabala',messageData:'[27条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/OIP.K068Qj2sIyhF7OAiAe1qVwHaEO?o=7rm=3&rs=1&pid=ImgDetMain&o=7&rm=3',name:'blashblash',messageData:'[30条]i need you!'},
    {imgUrl:$rawfile('myown.jpg'),name:'zhouhaoyang',messageData:'[30条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/R.3f505e222d848cf935ae5463ced6b7be?rik=X4jD3uI%2fMiCziA&riu=http%3a%2f%2fi1.hdslb.com%2fbfs%2farchive%2f84201a88b395fa4a547961f2c45d1957e2b25631.jpg&ehk=Aca2Rr8PRcsWGgxPa%2f%2fUHQpk6pWK9FA9KFchTjf0awQ%3d&risl=&pid=ImgRaw&r=0',name:'balabala',messageData:'[27条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/OIP.K068Qj2sIyhF7OAiAe1qVwHaEO?o=7rm=3&rs=1&pid=ImgDetMain&o=7&rm=3',name:'blashblash',messageData:'[30条]i need you!'},
    {imgUrl:$rawfile('myown.jpg'),name:'zhouhaoyang',messageData:'[30条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/R.3f505e222d848cf935ae5463ced6b7be?rik=X4jD3uI%2fMiCziA&riu=http%3a%2f%2fi1.hdslb.com%2fbfs%2farchive%2f84201a88b395fa4a547961f2c45d1957e2b25631.jpg&ehk=Aca2Rr8PRcsWGgxPa%2f%2fUHQpk6pWK9FA9KFchTjf0awQ%3d&risl=&pid=ImgRaw&r=0',name:'balabala',messageData:'[27条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/OIP.K068Qj2sIyhF7OAiAe1qVwHaEO?o=7rm=3&rs=1&pid=ImgDetMain&o=7&rm=3',name:'blashblash',messageData:'[30条]i need you!'},  {imgUrl:$rawfile('myown.jpg'),name:'zhouhaoyang',messageData:'[30条]i love you!'},
    {imgUrl:'https://th.bing.com/th/id/R.3f505e222d848cf935ae5463ced6b7be?rik=X4jD3uI%2fMiCziA&riu=http%3a%2f%2fi1.hdslb.com%2fbfs%2farchive%2f84201a88b395fa4a547961f2c45d1957e2b25631.jpg&ehk=Aca2Rr8PRcsWGgxPa%2f%2fUHQpk6pWK9FA9KFchTjf0awQ%3d&risl=&pid=ImgRaw&r=0',name:'balabala',messageData:'[27条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/OIP.K068Qj2sIyhF7OAiAe1qVwHaEO?o=7rm=3&rs=1&pid=ImgDetMain&o=7&rm=3',name:'blashblash',messageData:'[30条]i need you!'},  {imgUrl:$rawfile('myown.jpg'),name:'zhouhaoyang',messageData:'[30条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/R.3f505e222d848cf935ae5463ced6b7be?rik=X4jD3uI%2fMiCziA&riu=http%3a%2f%2fi1.hdslb.com%2fbfs%2farchive%2f84201a88b395fa4a547961f2c45d1957e2b25631.jpg&ehk=Aca2Rr8PRcsWGgxPa%2f%2fUHQpk6pWK9FA9KFchTjf0awQ%3d&risl=&pid=ImgRaw&r=0',name:'balabala',messageData:'[27条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/OIP.K068Qj2sIyhF7OAiAe1qVwHaEO?o=7rm=3&rs=1&pid=ImgDetMain&o=7&rm=3',name:'blashblash',messageData:'[30条]i need you!'},  {imgUrl:$rawfile('myown.jpg'),name:'zhouhaoyang',messageData:'[30条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/R.3f505e222d848cf935ae5463ced6b7be?rik=X4jD3uI%2fMiCziA&riu=http%3a%2f%2fi1.hdslb.com%2fbfs%2farchive%2f84201a88b395fa4a547961f2c45d1957e2b25631.jpg&ehk=Aca2Rr8PRcsWGgxPa%2f%2fUHQpk6pWK9FA9KFchTjf0awQ%3d&risl=&pid=ImgRaw&r=0',name:'balabala',messageData:'[27条]heiheihei'},
    {imgUrl:'https://th.bing.com/th/id/OIP.K068Qj2sIyhF7OAiAe1qVwHaEO?o=7rm=3&rs=1&pid=ImgDetMain&o=7&rm=3',name:'blashblash',messageData:'[30条]i need you!'},
  ]
  build() {
    List(){
      ForEach(this.messageList,(item:message)=>{
        // UI组件
        ListItem(){
          Row(){
            Image(item.imgUrl).width(50).height(50)
              .margin({right:20})
            Column(){
              Text(item.name)
              Text(item.messageData)
            }.alignItems(HorizontalAlign.Start)
          }
          // .border({width:2})
          .width('100%')
          .justifyContent(FlexAlign.Start)
          .padding(3)
          .border({width:{bottom:2}})
        }
        .width('100%')
      })

    }  // 分组
    // ListItemGroup()
    .width('100%')
    .height('100%')
    .border({width:'2'})
  }
}
```

---

## 15. Margin and Padding

```ts
@Entry
@Component
struct MarginPadding{

  build(){
    Column(){
      Text()
        // .width(80)
        // .height(80)
        // //外边框
        .margin({top:50,left:50,right:50,bottom:20})
        .width('100%')
        .height('100%')
        .backgroundColor(Color.Black)

    }
    .width(200)
    .height(200)
    .backgroundColor(Color.Pink)
    //边框
    .border({width:2,color:Color.Red})
    .padding(90)
  }
}
```

---

## 16. 自定义组件、aboutToAppear and Span

```ts
@Entry
@Component
struct Method{

  // 页面被构建前 拿取数据
  aboutToAppear(): void {
    // 逻辑
  }

  build() {
    Column(){
      // 文本显示组件
      Text('吉林大学')
      // 属性方法  字体大小、宽度、颜色 点链式方法引用
        .fontColor(Color.Blue)
        .fontSize(50)
        // 事件方法 用于做逻辑操作
        //点击事件
        .onClick(()=>{
          //逻辑
        })

      Text('55230121周浩洋')
        .fontColor(Color.Black)
        .fontSize(30)

      //自定义组件
      Method3()
      Method3()
    }
  }
}

@Preview
@Component
struct Method3{
  build() {
    Text(){
      Span('想要').fontSize(30).fontColor(Color.Black)
      Span('100').fontColor(Color.Red).fontSize(40)
      Span('分').fontSize(30).fontColor(Color.Black)
    }
  }

}

//没有入口文件
@Preview
@Component
struct Method2{

  build() {

    // 文本显示组件
    Text('你干嘛')
    // 属性方法  字体大小、宽度、颜色 点链式方法引用
      .fontColor(Color.Blue)
      .fontSize(50)
      // 事件方法 用于做逻辑操作
      //点击事件
      .onClick(()=>{
        //逻辑
      })
  }
}
```

---

## 17. Router

```ts
import router from '@ohos.router'

@Entry
@Component
struct Router{
  // 路由练习
  build() {
    Column(){
      Button('跳转')
        .onClick(()=>{
          router.pushUrl({url:'pages/Index'}) // stack，跳转后想返回
          // router.back() // 返回上一页，但只能和pushUrl联用
          // router.replaceUrl({url:'pages/CommonTest'}) //删除，跳转后不会返回
        })
    }
  }
}
```

```ts
// Index.ets

import router from '@ohos.router';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Button('返回上一页')
        .onClick(()=>{
          router.back()
        })
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

---



## 18. Preferences 持久化存储

```ts
// 第一步
// 用户首选项练习
// 导入@kit.ArkData模块
import {preferences} from '@kit.ArkData'
import {Content} from '@kit.ArkUI'
// 第二步 定义一个全局状态
let dataPreferences : preferences.Preferences | null =null;

@Entry
@Component
struct PreferencesTest{
  // 第三步 获取Preferences实例
  aboutToAppear(): void {
    dataPreferences = preferences.getPreferencesSync(getContext(Content),{name:'mystore'})
  }

  build() {
    Column(){
      Button('存储 school(key) name(value) 为 吉林大学')
        .onClick(()=>{
          //第四步 通过实例调用内置方法
          dataPreferences?.putSync('school','吉林大学')
          // 持久化存储
          dataPreferences?.flush()
        })
      Button('读取 school(key) name(value) 为 吉林大学')
        .onClick(()=>{
          console.log('jida    值为:'+ dataPreferences?.getSync('school',''))
        })
    }

  }
}
```

---

## 19. sql

```ts
import { relationalStore } from '@kit.ArkData'
import {Content} from '@kit.ArkUI'
// 全局数据库对象
let rdbStore: relationalStore.RdbStore | null = null

// 数据库配置信息
const store:relationalStore.StoreConfig ={
  name:'jidaDB',
  securityLevel:relationalStore.SecurityLevel.S3
}

// 建表
const sqlUser =
  'create table if not exists USER(ID integer primary key autoincrement,name text not null ,age integer)'

@Entry
@Component
struct SqlTest{

  //页面构建前获取实例
  aboutToAppear(): void {
    this.getjidaDB()
  }

  async getjidaDB(){
    rdbStore = await relationalStore.getRdbStore(getContext(Content),store)
    rdbStore.executeSql(sqlUser)
  }

  async insertNum():Promise<number>{
    if (rdbStore) {
      // 插入数据，返回 rowId
      return await rdbStore.insert('USER', { name: '吉林大学', age: 20 })
    }
    return -1 // 如果数据库未初始化，返回负数表示失败
  }
  build(){
    Column(){
      Button('存储')
        .onClick(async () => {
          // 使用 await 等待异步操作完成
          let num: number = await this.insertNum()
          if (num != -1) {
            AlertDialog.show({ message: '插入成功了' })
          } else {
            AlertDialog.show({ message: '插入失败了' })
          }
        })
    }
  }
}
```

## 20. Button、Checkbox、CheckboxGroup、DataPanel、Image、LoadingProgress、QRCode、Select和TextInput组件

```ts
@Entry
@Component
// 所有的常用组件
struct CommonTest{
  @State num : number = 0
  build(){
    // 一个容器组件根节点
    Scroll(){
      Column(){
        Button('按钮'+this.num)
          .type(ButtonType.Normal)
          .fontSize(50)
          .border({width:5})
          .borderRadius(20)
        // 多选框
        Checkbox()
        // 是否选中事件
        Checkbox()
          .onChange((flag : boolean)=>{
            console.log('jida '+flag)
          })
        Text('群组')
        // 群组
        CheckboxGroup({group:'check'})
        Checkbox({group:'check',name:'checkbox1'})
        Checkbox({group:'check',name:'checkbox2'})
        Checkbox({group:'check',name:'checkbox3'})

        .onChange((value)=>{
          console.log('jida     '+JSON.stringify(value))
        })

        Text('数据看板')
        DataPanel({values:[20,50,10,10,10],max:100,type:DataPanelType.Circle})
          .width(200)
          .height(200)
        DataPanel({values:[20,50,10,10,10],max:100,type:DataPanelType.Line})
          .width(200)
          .height(20)
        Text('图片')
        Image($rawfile('myown.jpg'))
          .height(200)
          .alignSelf(ItemAlign.Center)
        // Image("https://cdn.pixabay.com/photo/2020/04/13/19/40/sun-5039871_1280.jpg")
        //   .height(200)
        //   .alignSelf(ItemAlign.Center)
        Text("动态加载")
        LoadingProgress()
          .width(80)
          .color(Color.Blue)
        Text('喜欢我就加我微信吧~')
        QRCode('my wechat')
        Text("下拉选择")
        Text("你是？")
        Select([
          {value:'izhou',icon:$rawfile('myown.jpg')},
          {value:'ikun',icon:'https://th.bing.com/th/id/R.3f505e222d848cf935ae5463ced6b7be?rik=X4jD3uI%2fMiCziA&riu=http%3a%2f%2fi1.hdslb.com%2fbfs%2farchive%2f84201a88b395fa4a547961f2c45d1957e2b25631.jpg&ehk=Aca2Rr8PRcsWGgxPa%2f%2fUHQpk6pWK9FA9KFchTjf0awQ%3d&risl=&pid=ImgRaw&r=0'},
          {value:'奶龙',icon:'https://th.bing.com/th/id/OIP.K068Qj2sIyhF7OAiAe1qVwHaEO?o=7rm=3&rs=1&pid=ImgDetMain&o=7&rm=3'}
        ])
          .value('izhou')
          .onSelect((value:number)=>{
            console.log("jida    "+value)
          })
        Text('span text')
        Text(){// 可以作为容器组件使用
          Span('If ')
          Span('you ')
          Span('an izhou?').fontColor(Color.Blue)
        }
        Text('输入框')
        TextInput({placeholder:'向我表达心意吧~'})
          .onChange((value:string)=>{
            console.log("jida   "+value)
          })
        // TextArea({placeholder:''})
        //   .onChange((value:string)=>{
        //     console.log("jida  "+value)
        //   })
      }
      .onClick(()=>{
        this.num++
      })
      .alignItems(HorizontalAlign.Center)
      .width('100%')
    }
    .scrollBar(BarState.On)
    .scrollBarWidth(20)

  }
}
```

