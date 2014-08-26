# Tek Kayıt Bulma (Find One)

JSON Objesi ile modelden tek kaydı döndürür/getirir.

```
GET /:model/:id
```

<!--
<table>
  <thead>
    <tr>
      <th colspan="2">Blueprint Routes</th>
    </tr>
    <tr>
      <th>Type</th>
      <th>URL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>REST</td>
      <td>
        <code>GET /:modelIdentity/:id</code>
      </td>
    </tr>
    <tr>
      <td>Shortcut</td>
      <td>
        <code>GET /:modelIdentity/findOne/:id</code>
      </td>
    </tr>
  </tbody>
</table>
-->

**findOne()** blueprint aksiyonu model'den (`:modelIdentity` verilerek) JSON objesi formatında tek bir kayıt döndürür.  Belirtilen `id` istenilen kaydın [birincil anahtar (primary key)](http://en.wikipedia.org/wiki/Unique_key) 'ıdır.

Socket isteği ile aksiyon tetiklendiği zaman, istek yapan socket geri dönen kayda "subscribed" (katılmış) olacaktır. Kayıt daha sonra güncellenir veya silinirse, değişiklikler socket'in istemci bilgilendirmesine bir mesaj göndermiş olacaktır.  Daha fazla bilgi için, bknz: [.subscribe()](/#/documentation/reference/websockets/resourceful-pubsub/subscribe.html)
.


### Parametreler

 Parametre                          | Tip                                     | Ayrıntılar
 ---------------------------------- | --------------------------------------- |:---------------------------------
 id<br/>*(required)*                | ((number))<br/>*-or-*<br/>((string))    | İstenilen kaydın birincil anahtarı (primary key) <br/><br/>örn: `/urun/7`
 callback                           | ((string))                              | Eğer özellikle, JSONP isteği belirtilmişse (JSON'un yerine) gönderilecektir. Bu client-side javascript fonksiyonunu çağırmak için kullanılan isimle aynıdır. Sonuçları geçirme: ilk (ve tek) argüman alıyor gibi<br/> <br/> örn: `?callback=myJSONPHandlerFn`

### Örnek
ID #1 olan satışı bul, Örn: `http://localhost:1337/satis/1`

#### Route
`GET /satis/1`


#### Beklenen Cevap

 ```json
 {
   "miktar": 49.99,
   "id": 1,
   "createdAt": "2013-10-18T01:22:56.000Z",
   "updatedAt": "2013-10-18T01:22:56.000Z"
 }
 ```

<docmeta name="uniqueID" value="FindOne259267">
<docmeta name="displayName" value="find one">

