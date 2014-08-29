# Kayıtları Bul (Find)

JSON obje dizisi ile, modelden kayıtların bir listesini döndürür/getirir.

```
GET /:model
```

Sonuçlar filtrelenmiş, sayfalanmış, blueprint yapılandırılma merkezli sıralanmış ve/veya istekte parametreler gönderilmiş olabilir.


Aksiyon br socket isteği ile tetiklendiği zaman, istek yapan socket geri dönen kayda "subscribed" (katılmış) olacaktır. Kayıt daha sonra güncellenir veya silinirse, değişiklikler socket'in istemci bilgilendirmesine bir mesaj göndermiş olacaktır. Daha fazla bilgi için, bknz: [Model.subscribe()](https://github.com/balderdashy/sails-docs/blob/master/reference/ModelMethods.md#subscriberequestrecordscontexts) .



### Parametreler

_Bütün parametreler opsiyoneldir._

 Parametre      | Tip          | Ayrıntılar
 -------------- | ------------ |:---------------------------------
 *              | ((string))   | Sonuçları belirli bir niteliğe göre filtrelemek için, modelinde tanımlanmış nitelik ile aynı isimde bir sorgu parametresi belirt  <br/> <br/> Örneğin, bizim `Satis` modelimiz bir **miktar** niteliğine sahip,  $99.99 'lık satislarin listesini döndürmek için `GET /satis?miktar=99.99` gönderebiliriz.
 where          | ((string))   | Belirli bir niteliğe göre filtrelemek yerine, `where` parametresini Waterline WHERE kriter objesi _(JSON tipinde)_ ile sağlayabilirsiniz.  Bu `contains`(içerir), `startsWith` (ileBaslar) ve diğer alt nitelik kriterleri ile `find()` sorgusundan daha güçlü avantajlar sağlar. <br/> <br/> örn: `?where={"name":{"contains":"theodore"}}`
 limit          | ((number))   | Geriye döndürülecek olan maksimum kayıt sayısı (sayfalama için yararlı). Varsayılan: 30. <br/> <br/> örn: `?limit=100`
 skip           | ((number))   | Es geçilecek kayıt sayısı (sayfalama için yararlı). <br/> <br/> örn: `?skip=30`
 sort           | ((string))   | Sıralama düzeni. Varsayılan olarak birincil anahtar (primary key) değeri ile artan sıralama yapar. <br/> <br/> örn: `?sort=lastName%20ASC`
 callback       | ((number))   | Eğer özellikle, JSONP isteği belirtilmişse (JSON'un yerine) gönderilecektir.  Bu client-side javascript fonksiyonunu çağırmak için kullanılan isimle aynıdır. Sonuçları geçirme: ilk (ve tek) argüman alıyor gibi<br/> <br/> örn: ?callback=my_JSONP_data_receiver_fn



### `find` Örneği

Veritabanındaki en yeni olan 30 satışı bul.

```json
[
 {
   "miktar": 49.99,
   "id": 1,
   "createdAt": "2013-10-18T01:22:56.000Z",
   "updatedAt": "2013-10-18T01:22:56.000Z"
 },
 {
   "miktar": 99.99,
   "id": 47,
   "createdAt": "2013-10-14T01:22:00.000Z",
   "updatedAt": "2013-10-15T01:20:54.000Z"
 }
]
```

**[jQuery](http://jquery.com/) Kullanarak:**

```javascript
$.get('/satis?sort=createdAt DESC', function (satislar) {
  console.log(satislar);
});
```

**[Angular](https://angularjs.org/) Kullanarak:**

```javascript
$http.get('/satis?sort=createdAt DESC')
.then(function (res) {
  var satislar = res.data;
  console.log(satislar);
});
```

**[sails.io.js](http://beta.sailsjs.org/#/documentation/reference/websockets/sails.io.js) Kullanarak:**

```javascript
io.socket.get('/purchase?sort=createdAt DESC', function (purchases) {
  console.log(purchases);
});
```

**[cURL](http://en.wikipedia.org/wiki/CURL) Kullanarak:**

```bash
curl http://localhost:1337/satis?sort=createdAt%20DESC
```

### Notlar

> + Yukarıdaki örnek "rest" blueprints'in etkin olduğunu varsayar, ve senin projende bir `Satis` modeli, boş bir `SatisController` olduğunu varsayar.  Bu şekilde hızlıca oluşturabilirsin::
>
>   ```bash
>   $ sails new foo
>   $ cd foo
>   $ sails generate api satis
>   ```

<docmeta name="uniqueID" value="Find290807">
<docmeta name="displayName" value="find where">

