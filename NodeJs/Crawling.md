# Crawling

## Definition

**Crawling**은 ```Internet```의 ```Stie```의 ```Page``` 데이터를 수집하는 것을 말한다. **Node**에서는 ```Data```를 긁어오는 것뿐만 아니라 사이트에서의 이벤트를 처리할 수도 있다.  
**NodeJs**로 ```Crawling```을 하는 이유는 우선 ```Js```의 코드가 간결하고 유연성이 높아 변경이 용이하기 때문이다. 또한 많은 라이브러리가 있어 제작에 큰 어려움이 없다.  

## Site Download Way

**Crawling**를 위해서는 ```Site```의 ```Address```를 알아야 하며 해당 페이지를 분석하는 능력이 필요하다.  

## Scraping

**HTML Data를 수집하고 특정 데이터를 추출, 가공하여 저장하는 행위를 말한다.**

### HTML Analyze

```html
<!-- Infomation.html -->

<html>
    <head>
        <title>Information Page</title>
    </head>
    <body>
        <table>
            <tr>
                <td>Hello Word!</td>
            </tr>
        </table>
    </body>
</html>
```

위와 같은 코드의 내용을 ```Crawling```해보자  

```javascript
//Crawling.js

//download module
var request('cheerio-httpcli');

//download url
var url = 'http://localhost/Informatnion.html';
var param = {};

//have to err process for download url
client.fetch(url, param, function(err, $, res){
    //err check
    if(err) {
        console.log("Error: " + err);
        return;
    }

    var body = $.html();
    console.log(body);
});
```

**Node**에서 실행

> $ node Crawling.js

노드에서 실행하게 되면 위의 ```Information.html```의 내용이 출력되게 된다.