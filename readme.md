# qq qun member analyze

## STEP 1 -- get member list

### usage:

1. open this url.

`http://qun.qq.com/member.html`

2. copy this code to your url bar

```javascript
javascript:qqGroupNumber = document.getElementById("groupTit").innerText.match("\\\((\\d+)\\\)$")[1]; document.body.innerHTML = "LOADING<style>*{text-align:center; font-size:4em}</style>"; var bkn = ( function (skey) { var hash = 5381; for (var i = 0, len = skey.length; i < len; ++i) hash += (hash << 5) + skey.charAt(i).charCodeAt(); return hash & 2147483647; })((document.cookie.split("; ") ).map( function(x){ return x.split("="); } ).filter( function(x){ return "skey" == x[0]; })[0][1]); var srcQunManage = "http://qun.qq.com/cgi-bin/qun_mgr/search_group_members?st=0&end=2000&gc=" + qqGroupNumber + "&bkn=" + bkn; var srcQunZone = "http://qun.qzone.qq.com/cgi-bin/get_group_member?groupid=" + qqGroupNumber + "&g_tk=" + bkn; var get = (function(url) { var xhr = new XMLHttpRequest(); xhr.open("get", url, false); xhr.send(); return xhr.responseText; }); var mem1 = JSON.stringify( (JSON.parse( get(srcQunManage) .replace(/([^{,:])"([^:,}])/gmi, "$1\\\"$2") ) )["mems"]); document.body.innerHTML = ( "LOADING<style>*{text-align:center; font-size:4em}</style>" + "<script>\n" + "mem1 = " + mem1 + ";\n" + "ele = document.body;\n" + "_Callback = function(json){\n" + "var csvCell = function(x){\n" + "if(typeof(x) === \"string\"){\n" +  "x = x.replace(/&lt;/g, \"<\")\n" +  " .replace(/&gt;/g, \">\")\n" +  " .replace(/&amp;/g, \"&\")\n" +  " .replace(/&quot;/g, '\"')\n" +  " .replace(/&apos;/g, \"'\");\n" + "return \"\\\"\".concat( x.replace(/\"/gmi, \"\\\"\\\"\") ).concat(\"\\\"\")\n" + "}\n" + "return \"\".concat(x)\n" + "};\n" + "mem2 = json[\"data\"][\"item\"];\n" + "mem1 = mem1.sort(function(a, b){return a[\"uin\"] > b[\"uin\"] && 1 ||-1;});\n" + "mem2 = mem2.sort(function(a, b){return a[\"uin\"] > b[\"uin\"] && 1 ||-1;});\n" + "output = mem1.map(\n" + "function(x, index){\n" + "return (\n" + "csvCell(x[\"uin\"]) + '\t' +\n" + "csvCell(x[\"card\"]) + '\t' +\n" + "csvCell(x[\"flag\"]) + '\t' +\n" + "csvCell(x[\"g\"]) + '\t' +\n" + "csvCell(x[\"join_time\"]) + '\t' +\n" + "csvCell(x[\"last_speak_time\"]) + '\t' +\n" + "csvCell(x[\"lv\"][\"level\"]) + '\t' +\n" + "csvCell(x[\"lv\"][\"point\"]) + '\t' +\n" + "csvCell(x[\"nick\"]) + '\t' +\n" + "csvCell(x[\"qage\"]) + '\t' +\n" + "csvCell(x[\"role\"]) + '\t' +\n" + "csvCell(x[\"tags\"]) + '\t' +\n" + "csvCell(mem2[index][\"iscreator\"]) + '\t' +\n" + "csvCell(mem2[index][\"ismanager\"]) + '\t' +\n" + "csvCell(mem2[index][\"nick\"]) + '\t' +\n" + "csvCell(mem2[index][\"uin\"])\n" + ");\n" + "}\n" + ").join(\"\\n\");\n" + "ele.innerHTML = \"<pre>\" + \"Q号\t群名片_短\t标记\t性别\t入群时间\t发言时间\t等级\t积分\t昵称\tQ龄\t身份\t标签\t群主\t管理\t群名片\tQ号_重复<br />\"+ output + \"</pre>\";\n" + "};\n" + "</script>\n" + "<script src='" + srcQunZone + "'></script>\n" ); //更新：2016年6月11日
```

3. press `enter`

you will get a text that splited by '\t'

4. copy the text into notepad



5. then copy the text from notepad to excel

6. okay

## STEP 2 -- analyze

// waiting for working...