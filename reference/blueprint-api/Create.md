# Kayıt Oluşturma

Senin veritabanında yeni bir model örneği oluşturup oluşturulan değerleri geri döndürür.

```
POST /:model
```



Nitelikler HTTP body içinde form-encoded olarak veya JSON formatında gönderilebilir.

Yeni oluşturulan örneği temsil eden JSON objesi ile yanıt verir.  Doğrulama hatası meydana gelirse, geçersiz nitelikler ile bir JSON tepkisi ve bir `400` durum kodu fırlatacaktır.

Ayrıca, bir `create` isteği dinleyen tüm socket'lere yayınlanmış olacaktır (Daha fazlası için bknz: [.watch()](https://github.com/balderdashy/sails-docs/blob/master/reference/ModelMethods.md#watchrequest)).

Socket isteği ile bir aksiyon tetiklenirse, istek soketi de oluşturulmuş yeni model örneğine katılmış olacaktır. Kayıt daha sonra güncellenir veya silinirse, değişiklikler socket'in istemci bilgilendirmesine bir mesaj göndermiş olacaktır . Daha fazla bilgi için bknz: .subscribe().

### Parametreler

 Parametre      | Tip                                                       | Detaylar
 -------------- | --------------------------------------------------------- |:---------------------------------
 *              | ((string))<br/>((number))<br/>((object))<br/>((array))    | `POST` (RESTful) isteğinde: yeni kayıtta bu değerleri ayarlamak için, body parametrelerini senin modelinde tanımlanmış nitelikler ile aynı isimde gönder.`GET` (shortcut) istekleri için, parametreleri query string ile ekle. <br/> <br/> İçiçe objeler ve gönderilmiş olan array'ler, onların <a>.create()</a> metoduna geçirildiği gibi gönderilir.
 callback       | ((string))                                                | Eğer özellikle, JSONP isteği belirtilmişse (JSON'un yerine) gönderilecektir. Bu client-side javascript fonksiyonunu çağırmak için kullanılan isimle aynıdır. Sonuçları geçirme: ilk (ve tek) argüman alıyor gibi<br/> <br/> e.g. `?callback=myJSONPHandlerFn`

### Örnekler

#### Bir kayıt (REST) oluştur

Hobisi "pickin" olan "AppleJack" adında bir midilli oluştur.

#### Route
`POST /pony`



#### Gönderilecek olan JSON (JSON Request Body)
```json
{
  "name": "AppleJack",
  "hobby": "pickin"
}
```

#### Örnek Cevap
```json
{
  "name": "AppleJack",
  "hobby": "pickin",
  "id": 47,
  "createdAt": "2013-10-18T01:23:56.000Z",
  "updatedAt": "2013-11-26T22:55:19.951Z"
}
```

#### Bir kayıt oluştur (shortcuts)

#### Route
`GET /pony/create?name=Shutterfly&best_pony=yep`

#### Beklenen Cevap

```javascript
{
 "name": "Shutterfly",
 "best_pony": "yep",
 "createdAt": "2014-02-24T21:02:16.068Z",
 "updatedAt": "2014-02-24T21:02:16.068Z",
 "id": 5
}

```


### Tek Yollu İlişki Örnekleri

Modeller arasında iki yol ile ilişkiler oluşturabilirsin.  Ya ilişkiyi varolan bir kayıt ile VEYA iki kaydıda aynı anda oluşturarak yapabilirsin.  Nasıl olduğunu görmen için örnekleri kontrol et.

Bu örnekler `Pet` ve `Pony` adında iki API varlığının olduğunu varsayar, ister el ile isterseniz [Sails CLI Tool](/#!documentation/reference/CommandLine/CommandLine.html) ile oluşturabilirsiniz. `Pony` modeli  `Pet` modelini işaret eden `pet` niteliği ile yapılandırılmış olması gereklidir. Bunun nasıl yapıldığını bilmek için bknz: [Model İlişki Dokümanları](./ModelAssociations.md).

### Varolan Kayıt ile İlişkilendirerek w/ Yeni Kayıt Oluştur (REST)

"Pinkie Pie" adında  bir midilli oluştur ve onu "Gummy" adında `id`'si 10 olan bir evcil hayvan ile ilişkilendir.

#### Route
`POST /pony`

#### Gönderilecek olan JSON (JSON Request Body)
```json
{
  "name": "Pinkie Pie",
  "hobby": "ice skating",
  "pet": 10
}
```

#### Beklenen Cevap
```json
{
  "name": "Pinkie Pie",
  "hobby": "ice skating",
  "pet": {
    "name": "Gummy",
    "species": "crocodile",
    "id": 10
  },
  "id": 4,
  "createdAt": "2013-10-18T01:22:56.000Z",
  "updatedAt": "2013-11-26T22:54:19.951Z"
}
```


### Yeni Kayıt ile İlişkilendirerek w/ Yeni Kayıt Oluştur (REST)

İsmi "Pinkie Pie" hobby'si "ice skating" ve "Gummy" adında evcil hayvan (pet) ile ilişkilendirilmiş yeni bir kayıt oluştur.

#### Route
`POST /pony`


#### Gönderilecek olan JSON (JSON Request Body)
```json
{
  "name": "Pinkie Pie",
  "hobby": "ice skating",
  "pet": {
    "name": "Gummy",
    "species": "crocodile"
  }
}
```

#### Beklenen Cevap
```json
{
  "name": "Pinkie Pie",
  "hobby": "ice skating",
  "pet": {
    "name": "Gummy",
    "species": "crocodile"
    "id": 10
  },
  "id": 4,
  "createdAt": "2013-10-18T01:22:56.000Z",
  "updatedAt": "2013-11-26T22:54:19.951Z"
}
```

<docmeta name="uniqueID" value="CreateARecord744986">
<docmeta name="displayName" value="create">

