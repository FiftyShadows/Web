```
//屏蔽右键菜单  
document.oncontextmenu = function (event){  
    if(window.event){  
        event = window.event;  
    }try{  
        var the = event.srcElement;  
        if (!((the.tagName == "INPUT" && the.type.toLowerCase() == "text") || the.tagName == "TEXTAREA")){  
            return false;  
        }  
        return true;  
    }catch (e){  
        return false;  
    }  
}  

//屏蔽粘贴  
document.onpaste = function (event){  
    if(window.event){  
        event = window.event;  
    }try{  
        var the = event.srcElement;  
        if (!((the.tagName == "INPUT" && the.type.toLowerCase() == "text") || the.tagName == "TEXTAREA")){  
            return false;  
        }  
        return true;  
    }catch (e){  
        return false;  
    }  
}  

//屏蔽复制  
document.oncopy = function (event){  
    if(window.event){  
        event = window.event;  
    }try{  
        var the = event.srcElement;  
        if(!((the.tagName == "INPUT" && the.type.toLowerCase() == "text") || the.tagName == "TEXTAREA")){  
            return false;  
        }  
        return true;  
    }catch (e){  
        return false;  
    }  
}  

//屏蔽剪切  
document.oncut = function (event){  
    if(window.event){  
        event = window.event;  
    }try{  
        var the = event.srcElement;  
        if(!((the.tagName == "INPUT" && the.type.toLowerCase() == "text") || the.tagName == "TEXTAREA")){  
            return false;  
        }  
        return true;  
    }catch (e){  
        return false;  
    }  
}  

//屏蔽选中  
document.onselectstart = function (event){  
    if(window.event){  
        event = window.event;  
    }try{  
        var the = event.srcElement;  
        if (!((the.tagName == "INPUT" && the.type.toLowerCase() == "text") || the.tagName == "TEXTAREA")){  
            return false;  
        }  
        return true;  
    } catch (e) {  
        return false;  
    }  
}

window.onbeforeunload = function(event){  
    event = event || window.event;  
    event.returnValue = ' ';  
}

//屏蔽类似iphone的默认滑动事件,禁用浏览器的默认滑动事件  
var preventBehavior = function(e) {  
    e.preventDefault();  
};  
// Enable fixed positioning  
document.addEventListener("touchmove", preventBehavior, false); 


*{   
    -webkit-touch-callout:none;  /*系统默认菜单被禁用*/   
    -webkit-user-select:none; /*webkit浏览器*/   
    -khtml-user-select:none; /*早期浏览器*/   
    -moz-user-select:none;/*火狐*/   
    -ms-user-select:none; /*IE10*/   
    user-select:none;   
}
//在IOS 上会有问题的，这个时候你会发现input 框无法正在输入了内容
input {      
    -webkit-user-select:auto; /*webkit浏览器*/     
}  
```