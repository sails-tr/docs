# Kayıt Silme (Destroy)

Daima veri tabanından varolan bir kaydı belirtilen `id`'ye göre siler ve silinmiş kaydı döndürür/getirir.

```
DELETE /:model/:record
```

**id** parametresi ile eşleşen model örneğini siler.  Silinen örneği temsil eden bir JSON objesi ile cevap verir.  Belirtilen **id** ile eşleşen bir kayıt yoksa, bir `404` geriye döndürür.

Ayrıca, bir `destroy` olayı tüm socket'lerin abonesi örnek odaya yayınlanmış olacaktır.

Sonuç olarak, şu anda örneğe abone olmuş tüm socket'Ler ondan habersiz kalacaktır.


### Parametreler

 Parametre                          | Tip                                     | Ayrıntılar
 ---------------------------------- | --------------------------------------- |:---------------------------------
 id<br/>*(gereklidir)*              | ((number))<br/>*-or-*<br/>((string))    | Kaydı silmek için birincil anahtar (primary key) değeri. `POST` (RESTful) istekleri için, JSON body ile verilmiştir veya rota yolunun (route path) bir parçasıyla. `GET` (shortcut) istekleri için, rota yolunun (route path) verilmiş olması gerekir.
 callback                           | ((string))                              | Eğer özellikle, JSONP isteği belirtilmişse (JSON'un yerine) gönderilecektir.  Bu client-side javascript fonksiyonunu çağırmak için kullanılan isimle aynıdır. Sonuçları geçirme: ilk (ve tek) argüman alıyor gibi<br/> <br/> örn: `?callback=myJSONPHandlerFn`

### Örnekler

#### Silme - Destroy (REST)

*Pinkie Pie* 'ı sil .

#### Route
`DELETE /pony`

#### Gönderilecek olan JSON (JSON Request Body)
```json
{
  "id": 4
}
```

#### Beklenen Cevap

```json
{
  "name": "Pinkie Pie",
  "hobby": "kickin",
  "id": 4,
  "createdAt": "2013-10-18T01:23:56.000Z",
  "updatedAt": "2013-11-26T22:55:19.951Z"
}
```

#### Silme - Destroy (Shortcuts)

#### Route
`GET /pony/destroy/4`

#### Beklenen Cevap

Yukarıdaki örnek ile aynı.


<docmeta name="uniqueID" value="DestroyARecord867513">
<docmeta name="displayName" value="destroy">

