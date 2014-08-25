# Koleksiyona Ekleme

İki kayıt arasına bir ilişki ekleme.

```
PUT /:model/:record/:association/:record_to_add
```

Bu aksiyon, koleksiyonun özelliği ("primary" (birincil) kayıt) üzerinden diğer kayda ("foreign" (yabancı) kayıt) referans ekler.

+ Yabancı (foreign) kayıt bulunmuyorsa, ilk olarak oluşturulur.
+ Eğer birincil (primary) kayıttaki kolleksiyon, yabancı (foreign) kayda referansı varsa bu eylem reddedilir.
+ Eğer ilişki 2-way (çift yollu) ise, (örn: dönüşümlü, her iki tarafta "via" ile) yabancı kayıttaki ilişki güncellenmiş olur.


### Örnek

Satışlar listesine Ahmed (id #7) isimli işçinin 47 nolu satşını ekle.

**[jQuery](http://jquery.com/) Kullanarak:**

```javascript
$.post('/isci/7/yapilanSatislar/47', function (purchases) {
  console.log(purchases);
});
```

**[Angular](https://angularjs.org/) Kullanarak:**

```javascript
$http.post('/isci/7/yapilanSatislar/47')
.then(function (purchases) {
  console.log(purchases);
});
```

**[sails.io.js](http://beta.sailsjs.org/#/documentation/reference/websockets/sails.io.js) Kullanarak:**

```javascript
io.socket.post('/isci/7/yapilanSatislar/47', function (purchases) {
  console.log(purchases);
});
```

**[cURL](http://en.wikipedia.org/wiki/CURL) Kullanarak:**

```bash
curl http://localhost:1337/isci/7/yapilanSatislar/47 -X "POST"
```


"Ahmed" birincil (primary) kayıt olarak dönmeli:

```json
{
  "yapilanSatislar": [
    {
      "miktar": 10000,
      "createdAt": "2014-08-03T01:50:33.898Z",
      "updatedAt": "2014-08-03T01:51:08.227Z",
      "id": 47,
      "kasiyer": 7
    }
  ],
  "isim": "Ahmed",
  "createdAt": "2014-08-03T01:16:35.440Z",
  "updatedAt": "2014-08-03T01:51:41.567Z",
  "id": 7
}
```


### Notlar

> + Bu eylem _çoğul_ ("koleksiyon") ilişki ile ilgilidir.  _tekil_ ("model") ilişkisi kurmak istiyorsan, [update](http://sailsjs.org/#/documentation/reference/blueprint-api/Update.html)'i kullanabilirsin.
> + Yukarıdaki örnek "rest" blueprints'in açık olduğunu ve senin projende en az bir 'Isci' modelinin ilişkilenmiş olduğunu varsayar: `yapilanSatislar: {collection: 'Satis', via: 'kasiyer'}` aynı zamanda `Satis` modeli `kasiyer: {model: 'Isci'}` ile ilişkilidir.  Ve senin en az boş bir tane `SatisController` ve `IsciController` 'a ihtiyacın olacak.  Bu şekilde hızlı bir şekilde oluşturabilirsin:
>
>   ```shell
>   $ sails new foo
>   $ cd foo
>   $ sails generate api satis
>   $ sails generate api isci
>   ```
>
> ...sonra `api/models/Satis.js` ve `api/models/Isci.js`'i düzelterek.

<docmeta name="uniqueID" value="Add262514">
<docmeta name="displayName" value="add to">
