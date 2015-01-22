tvQuery
tvQuery用于电视端开发的TV组件。
参考了jQuery的实现方法，主要模拟了按钮、文本框、下拉框、radio、checkbox等组件。
另外用js实现了一个支持中文输入法的键盘，还有一些其它扩展组件，如城市选择等功能，
联动下拉框，图片切换、评价、中文翻页等。
由于用到一些CSS3的特性，所以在浏览器上使用时请使用支持CSS3的浏览器。
tvQuery模拟了jQuery的调用方法，可以给组件元素绑定事件，添加属性。
另支持ajax，alert框，confirm框等。

API如下所示:

//所有组件都有的方法:

$tv('#id').left(function(){});  左移之前调用的方法

$tv('#id').right(function(){}); 右移之前调用的方法

$tv('#id').down(function(){});  下移之前调用的方法

$tv('#id').up(function(){});    上移之前调用的方法

$tv('#id').loseFocus(function(){});  失去焦点之前调用的方法

$tv('#id').getFocus(function(){});   得到焦点之前调用的方法

//按钮组件
$tv('#id').ok(function(){});   确认方法

$tv('#id').attr('tv_css',[])   添加属性方法

按钮可添加的属性有x,y,tv_css

//文本框和密码组件框

$tv('#id').val();    取值

$tv('#id').val(12);  赋值

$tv('#id').attr('tv_css',[])    添加属性方法

$tv('#id').attr('maxlength',10) 添加文本框输入字符个数

文本框可添加的属性有x,y,tv_css,maxlength,placeholder,content(number)

//文本框有键盘事件

$tv('#id').ok(function(){this.bindSoftKey()})//按OK键可以调用

//下拉框

$tv('#id').val();    取值

$tv('#id').val(12);  赋值

$tv('#id').attr('tv_css',[])

$tv('#id').attr('option',[])

下拉框可添加的属性有x,y,tv_css,option

//单选框

$tv('.color').val();

$tv('.color').val('value');

$tv('#id').attr('tv_css',[])

$tv('#id').attr('name','color')

$tv('#id').attr('value',21)

$tv('#id').attr('tv_css',[]).attr('name','color').attr('value',21) 支持连写

$tv('#id').attr({'tv_css':[],'name':'color','value':21}); 支持一次添加所有属性

单选框可添加的属性有x,y,tv_css,name,value

//多选框

$tv('.color').val();

$tv('.color').val('value1,value2');

$tv('#id').attr('tv_css',[])

$tv('#id').attr('name','color')

$tv('#id').attr('value',21)

多选框可添加的属性有x,y,tv_css,name,value

//特殊组件tv_special 

$tv('#id').doKeyBoardMethod(function(){}) //键盘方法，支持数字键，字母键操作

$tv('#id').doKeyBoardMethod(function(){

	switch (this.key){
	
		case 1 :{
		
			doSomething(); //按下数字键1时执行方法
			
			break;
			
		} 
		
		case 2 :{
		
			doSomething(); //按下数字键2时执行方法
			
			break;
		} 
		
		...
		
	}
    });

$tv.loadInit({id:'tv_classify',data:data})   初始化方法，并将焦点放到id上

$tv.setSupportMouse(false);          		 禁止鼠标事件,$tv.setSupportMouse(true);支持

$tv.alert('内容');  				 alert框

$tv.setFocusId('id');                		 设置焦点

$tv.tvLoad(oDiv,data);                    	 加载新的div,主要用于display:none这种div显示的时候调用

//confirm框

$tv.confirm({		
	content:'确定要删除这个吗？',
	
	onClose:function(v){
	
		if(v){
		
			alert('确认');
			
		}else{
		
			alert('取消');
			
		}
		
	}
	
    });

//ajax方法

$tv.ajax({

	url: "http://192.168.1.59/TV_Component/index.html",  //请求地址
	
	type: "GET",                       //请求方式
	
	data: {name: "super", age: 20 },   //请求参数
	
	dataType: "json",
	
	success: function (response, xml) {
	
		alert(response);
		
	},
	
	fail: function (status) {
	
		// 此处放失败后执行的代码
		
	}
});

//扩展组件

//评分组件

star.init('tv_star',3); //初始化可评分

star.info('tv_star',3); //只显示评分级别

$tv('#tv_star').val();  //获取评分

//翻页组件

var obj ={

	id:'infoText', //需翻页的ID
	
	preId:"tv_pre", //上一页按钮ID
	
	nextId:'tv_next' //下一页按钮ID	
	
}

pageTurn.init(obj);

//中文键盘组件 （其中tv_search_text为文本框，right,bottom为键盘位置）

$tv('#tv_search_text').ok(function(){this.bindSoftKey({right:'10px',bottom:'10px'})})

//联动下拉组件

var obj = {		

	css1:['one_select_1','one_select_2'],//有右键头
	
	css2:['two_select_1','two_select_2'],//没右键头	
	
	data:[
	
		{one:{id:'0',name:'全部分类',level:0}},
		
		{one:{id:'1',name:'美食'},
		
		 two:[{	id:'1',name:'火锅'},
			 
		     	{id:'1',name:'自助餐'},
		     
		     	{id:'1',name:'西餐'},
			  
		     	{id:'1',name:'日韩料理'},
			  
			{id:'1',name:'蛋糕甜点'},
			  
		  	{id:'1',name:'烧烤烤鱼'},
			  
		  	{id:'1',name:'川湘菜'},
			  
		  	{id:'1',name:'江浙菜'},
			  
		  	{id:'1',name:'京菜'},
			  
		  	{id:'1',name:'素食'},
			  
  			{id:'1',name:'清真菜'},
			  
		  	{id:'1',name:'台湾菜'},
			  
		  	{id:'1',name:'特色菜'},
			  
		  	{id:'1',name:'咖啡酒吧'},
			  
		  	{id:'1',name:'其它美食'}]},
			  
		{one:	{id:'2',name:'酒店',level:0},
		
		 two:[	{id:'2',name:'经济型酒店'},
		 
	 	  	{id:'2',name:'豪华酒店'}]},
		 	  
		{one:	{id:'3',name:'电影'}},
		
		{one:	{id:'4',name:'休闲娱乐'},
		
		 two:[	{id:'4',name:'电影'},
		 
		 	{id:'4',name:'KTV'},
			 
		 	{id:'4',name:'温泉/洗浴'},
			 
		 	{id:'4',name:'足疗按摩'},
			 
		 	{id:'4',name:'运动健身'},
			 
		 	{id:'4',name:'桌游/电玩'},
			 
		 	{id:'4',name:'密室逃脱'},
			 
		 	{id:'4',name:'咖啡酒吧'},
			 
		 	{id:'4',name:'演出赛事'},
			 
		 	{id:'4',name:'DIY手工'},
			 
		 	{id:'4',name:'真人CS'},
			 
		 	{id:'4',name:'4D/5D电影'},
			 
		 	{id:'4',name:'其它娱乐'}]},
			 
		{one:	{id:'5',name:'生活服务'},
		
		 two:[	{id:'5',name:'母婴亲子'},
		 
		 	{id:'5',name:'摄影写真'},
			 
		 	{id:'5',name:'体检保健'},
			 
		 	{id:'5',name:'汽车服务'},
			 
		 	{id:'5',name:'照片冲印'},
			 
		 	{id:'5',name:'培训课程'},
			 
		 	{id:'5',name:'鲜花婚庆'},
			 
		 	{id:'5',name:'服饰服务'},
			 
		 	{id:'5',name:'配镜'},
			 
		 	{id:'5',name:'其它生活'}]},
			 
		{one:	{id:'6',name:'丽人'},
		
		 two:[	{id:'6',name:'美发'},
		 
		 	{id:'6',name:'美甲'},
			 
		 	{id:'6',name:'美容SPA'},
			 
		 	{id:'6',name:'瑜伽/舞蹈'}]},
			 
		{one:	{id:'7',name:'旅游'},
		
		 two:[	{id:'7',name:'本地/周边游'},
		 
	 	 	{id:'7',name:'景点门票'}]
		 	 
		}
		
	]
	
}

$tv('#tv_classify').ok(function(){linkSelect.init(this.id,obj)});

//地区选择组件

$tv('#tv_location').ok(function(){tvArea.init(this.id);});

   
