/*
*  解析URL中参数
*  @example：?id=12345&a=b
*  @return Object{id:12345,a:b}
* */
function urlParse() {
    //获取到?id=12345&a=b
    let url = window.location.search;           
    let obj = {};
    //匹配所有?id=12345或&a=b
    let reg = /[?&][^?&]+=[^?&]+/g;          
    let arr = url.match(reg);
    if (arr) {
        arr.forEach((item) => {
            //去掉第一个？&字符，将字符串用等号分隔的分开扔进数组
            let tempArr = item.substring(1).split('=');
            //key = id
            let key = decodeURIComponent(tempArr[0]);
            //calue = 12345
            let val = decodeURIComponent(tempArr[1]);
            obj[key] = val;
        });
    }
    return obj;
};
