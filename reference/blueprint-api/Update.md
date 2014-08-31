# Kaydı Güncelleştirme

### `PUT /:model/:record`

Varolan bir kaydı güncellemek için: Değiştirilmek istenen nitelikler, HTTP body içinde form-encoded değerleriyle veya JSON formatında gönderilmiş olmalıdır. 

### Açıklama
**id** parametresi ile eşleşen model örneğini günceller. Güncellenen kaydın bir örneği JSON object şeklinde gösterir.
Doğrulama hatası meydana gelirse, geçersiz nitelikler ile bir JSON tepkisi ve bir 400 durum kodu fırlatacaktır.  **id** ile eşleşen model örneği yoksa, bir `404` döner.

### Parametreler

 Parametre                          | Tip                                                    | Ayrıntılar
 ---------------------------------- | ------------------------------------------------------- |:---------------------------------
 id<br/>*(gerekli)*                 | ((number))<br/>*-veya-*<br/>((string))                  | Güncellemek için kaydın birincil anahtarı (primary key).<br/><br/>örn: `PUT /product/5`
 *                                  | ((string))<br/>((number))<br/>((object))<br/>((array))  | POST (RESTful) isteğinde: İstenilen kayıt üzerindeki bu değerleri ayarlamak için, body parametrelerini modelinde tanımlanmış olan nitelik ismiyle aynı isimde gönder. `GET` (shortcut) istekleri için, parametreleri query string ile ekle.
 callback                           | ((string))                                              | Eğer özellikle, JSONP isteği belirtilmişse (JSON'un yerine) gönderilecektir. Bu client-side javascript fonksiyonunu çağırmak için kullanılan isimle aynıdır. Sonuçları geçirme: ilk (ve tek) argüman alıyor gibi<br/> <br/> örn: `?callback=myJSONPHandlerFn`

### Örnekler

### Kaydı Güncelle (REST)

AppleJack'in hobisini "kickin" ile değiştir.

#### Route
`PUT /pony/47`

#### Gönderilecek olan JSON (JSON Request Body)
```json
{
  "hobby": "kickin"
}
```

### Beklenen Cevap
```json
{
  "name": "AppleJack",
  "hobby": "kickin",
  "id": 47,
  "createdAt": "2013-10-18T01:23:56.000Z",
  "updatedAt": "2013-11-26T22:55:19.951Z"
}
```

### Kısayolu Güncelle (Shortcuts) 

`GET /pony/update/47?hobby=kickin`

#### Beklenen Cevap

Yuardakiyle aynı.

### Varolan iki kayıt arasına ilişki ekle (REST)

Pinkie Pie'e, önceden mevcut pet adı "Bubbles", ID'si 15 olan kaydı ver.
Give Pinkie Pie the pre-existing pet named "Bubbles" who has ID 15.

#### Route
`POST /pony/4/pets`

#### Gönderilecek olan JSON (JSON Request Body)
```json
{
  "id": 15
}
```

#### Beklenen Cevap
```json
{
  "name": "Pinkie Pie",
  "hobby": "kickin",
  "id": 4,
  "pets": [{
      "name": "Gummy",
      "species": "crocodile"
      "id": 10,
      "createdAt": "2014-02-13T00:06:50.603Z",
      "updatedAt": "2014-02-13T00:06:50.603Z"
    },{
      "name": "Bubbles",
      "species": "wiggleworm"
      "id": 15,
      "createdAt": "2014-02-13T00:06:50.603Z",
      "updatedAt": "2014-02-13T00:06:50.603Z"
    }],
  "createdAt": "2013-10-18T01:23:56.000Z",
  "updatedAt": "2013-11-26T22:55:19.951Z"
}
```

### Varolan iki kayıt arasına ilişki kısayolu ekle (Shortcuts)
`GET /pony/4/pets/add/15`

### İlişkiyi sil (Many-To-Many) (REST)

Pinkie Pie'nin pet'ini sil, "Gummy" (ID 12)

#### Route
`DELETE /pony/4/pets`

#### Gönderilecek olan JSON (JSON Request Body)
```json
{
  "id": 12
}
```

#### Beklenen Cevap
```json

{
  "name": "Pinkie Pie",
  "hobby": "ice skating",
  "pets": [{
      "name": "Bubbles",
      "species": "crackhead"
      "id": 15,
      "createdAt": "2014-02-13T00:06:50.603Z",
      "updatedAt": "2014-02-13T00:06:50.603Z"
    }],
  "id": 4,
  "createdAt": "2013-10-18T01:22:56.000Z",
  "updatedAt": "2013-11-26T22:54:19.951Z"
}

```

#### İlişkiyi sil (Many-To-Many) (Shortcuts)

#### Route

`GET /pony/4/pets/remove/12`

#### Beklenen Cevap

Yukardaki ile aynı.

<docmeta name="uniqueID" value="UpdateARecord421031">
<docmeta name="displayName" value="update">

