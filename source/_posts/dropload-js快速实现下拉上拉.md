---
title: dropload.js快速实现下拉上拉
date: 2020-06-12 16:44:00
tags: js库
---


1. 引入js
```
<script src="js/dropload.js" type="text/javascript" charset="utf-8"></script>
```

2. 页面配置
```
    // 最外层容器class
    $('.content').dropload({
        scrollArea : window,
        domUp : {
            domClass   : 'dropload-up',
            domRefresh : '<div class="dropload-refresh">↓下拉刷新-自定义内容</div>',
            domUpdate  : '<div class="dropload-update">↑释放更新-自定义内容</div>',
            domLoad    : '<div class="dropload-load"><span class="loading"></span>加载中-自定义内容...</div>'
        },
        domDown : {
            domClass   : 'dropload-down',
            domRefresh : '<div class="dropload-refresh">↑上拉加载更多-自定义内容</div>',
            domLoad    : '<div class="dropload-load"><span class="loading"></span>加载中-自定义内容...</div>',
            domNoData  : '<div class="dropload-noData">暂无数据-自定义内容</div>'
        },
        loadUpFn : function(me){
            $.ajax({
                type: 'GET',
                url: 'json/update.json',
                dataType: 'json',
                success: function(data){
                    var result = '';
                    
                    // 为了测试，延迟1秒加载
                    setTimeout(function(){
                        $('.lists').html(result);
                        // 每次数据加载完，必须重置
                        me.resetload();
                        // 重置页数，重新获取loadDownFn的数据
                        page = 0;
                        // 解锁loadDownFn里锁定的情况
                        me.unlock();
                        me.noData(false);
                    },1000);
                },
                error: function(xhr, type){
                    alert('Ajax error!');
                    // 即使加载出错，也得重置
                    me.resetload();
                }
            });
        },
        loadDownFn : function(me){
            page++;
            // 拼接HTML
            var result = '';
            $.ajax({
                type: 'GET',
                url: 'http://url?page='+page+'&size='+size,
                dataType: 'json',
                success: function(data){
                    // 渲染
                    // 每次数据插入，必须重置
                        me.resetload();
                    // 如果没有数据
                    }else{
                        // 锁定
                        me.lock();
                        // 无数据
                        me.noData();
                    }
                },
                error: function(xhr, type){
                    alert('Ajax error!');
                    // 即使加载出错，也得重置
                    me.resetload();
                }
            });
        },
        threshold : 50
    });
```
[API地址](https://github.com/ximan/dropload)


#### 遇到了一个问题，第一次下拉正常，第二次无法下拉

获取到数据以后，innerHtml的节点不能是dropload绑定的节点，要是dropload绑定节点的子节点