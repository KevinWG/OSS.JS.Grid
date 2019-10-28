﻿## OSS.Grid

一.使用方式：
```js
 var opt = { displayHeader: true,
  page:
  {
     is_page: true,
     size: 8,
     cur_page: 1
  },

  container: {
     header: "",
     content: "",
     footer: ""
  },

  methods: {
    // 扩展post之前的参数
    extSendParas: function () { return {}; },
    //  获取数据源方法
    getDataFunc: function (pageData, loadDataFunc) {
		$.post("/ajax/url",pageData,function(res){
			loadDataFunc(res);
        })  
    },
    //数据绑定完成之后
    dataBound: function () { }
  }
}

$("#container").osstable(opt)
```


## OS.Tree

一. 使用方式：
```js
  var opt = {
  textField: "name",
  valueField: "id",
  parentField: "parentId",

  isRemote: false,     //  是否远程加载，子节点会延迟渲染
  isDeferred: false,   //  是否延迟加载，isRemote=true 时，isDeferred 恒为 true
  isOpen: false,       //  首次加载是否全部展开状态,isDeferred=true时，isOpen 恒为 false

  methods: {
      //  获取数据源方法
      getSource: function(proNode, callBack) {
          var treeData = [
              { id: 1, name: "ceshi1", parentId: 0 },
              { id: 2, name: "ceshi2", parentId: 1 },
              { id: 3, name: "ceshi3", parentId: 0 },
              { id: 4, name: "ceshi4", parentId: 2 }
          ];
          callBack(treeData);
      },

      //  选中事件
      chosen: function (dataItem, element) {
          console.info("chosen");
          console.info(dataItem);
          //alert("被选中了！");
      },
      //  每一个层级执行完成之后事件
      dataBound: function(data, element) {
          //alert("层级绑定完毕");
          console.info("dataBound");
          console.info(data);
      },
      //  绑定每个对象时触发
      dataBounding: function (dateItem, leaf) {
          console.info("dataBounding");
          console.info(dateItem);
      }
  }
 }
 $(function () {
     $("#treeContainer").ostree(opt);
 });
```