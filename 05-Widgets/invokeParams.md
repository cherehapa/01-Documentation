# Передача параметров в большой виджет в новом коде для вставки

Без возраста туристов:
```
<script class="cheScrpt" type="text/javascript">
    var widget=widget||[];options={
	"partnerId":1,
	"widgetId":1,
	"invokeParams":{"country_name":"Япония","date_start":"19.12.2015","date_end":"18.01.2016", "tourists" :"3"}
	};
    (function(s, w, o, d, i, h){w.push(o); if(d.getElementById(i))return;
        var cjs=d.getElementsByTagName(h)[0];var js = d.createElement(s);
        js.id = "cheWidgetScrpt";js.type = "text/javascript"; js.async = true;
        js.src = "//d2j2dl4huu79en.cloudfront.net/s/2.0.2/widget.min.js";cjs.appendChild(js);
    })('script', widget, options, document, 'cheWidgetScrpt', 'head');
</script>
```

С возрастом туристов:
```
<script class="cheScrpt" type="text/javascript">
    var widget=widget||[];options={
	"partnerId":1,
	"widgetId":1,
	"invokeParams":{"country_name":"Япония", "date_start":"19.12.2015","date_end":"18.01.2016", "tourists" :"3", "tourist_0" : "10", "tourist_1" : "40", "tourist_2" : "20"}
	};
    (function(s, w, o, d, i, h){w.push(o); if(d.getElementById(i))return;
        var cjs=d.getElementsByTagName(h)[0];var js = d.createElement(s);
        js.id = "cheWidgetScrpt";js.type = "text/javascript"; js.async = true;
        js.src = "//d2j2dl4huu79en.cloudfront.net/s/2.0.2/widget.min.js";cjs.appendChild(js);
    })('script', widget, options, document, 'cheWidgetScrpt', 'head');
</script>
```

С множественными странами - не выходит.
