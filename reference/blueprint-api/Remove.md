# Koleksiyondan Sil

İki kayıt arasındaki ilişkiyi(association) siler.

```
DELETE /:model/:record/:association/:record_to_remove
```

Bu aksiyon bu kayıtın koleksiyon niteliğinden ("primary" (birincil) kayıt) diğer kayıta olan bir referansı ("foreign" (yabancı) kayıt) siler. 
.

+ Yabancı (foreign) kayıt bulunmuyorsa, ilk olarak oluşturulur.
+ Eğer birincil (primary) kayıttaki kolleksiyon, yabancı (foreign) kayda referansı varsa bu eylem reddedilir.
+ Eğer ilişki 2-way (çift yollu) ise, (örn: dönüşümlü, her iki tarafta "via" ile) yabancı kayıttaki ilişki güncellenmiş olur.


### Örnek

#16 nolu depoda (store) olan Dolly 'yi (isci #7) `employeesOfTheMonth` 'dan sil.

**[jQuery](http://jquery.com/) Kullanarak:**

```javascript
$.delete('/store/16/employeesOfTheMonth/7', function (purchases) {
  console.log(purchases);
});
```

**[Angular](https://angularjs.org/) Kullanarak:**

```javascript
$http.delete('/store/16/employeesOfTheMonth/7')
.then(function (purchases) {
  console.log(purchases);
});
```

**[sails.io.js](http://beta.sailsjs.org/#/documentation/reference/websockets/sails.io.js) Kullanarak:**

```javascript
io.socket.delete('/store/16/employeesOfTheMonth/7', function (purchases) {
  console.log(purchases);
});
```

**[cURL](http://en.wikipedia.org/wiki/CURL) Kullanarak:**

```bash
curl http://localhost:1337/store/16/employeesOfTheMonth/7 -X "DELETE"
```


Should return store #16, the primary record:

```json
{
  "employeesOfTheMonth": [],
  "name": "Dolly",
  "createdAt": "2014-08-03T01:16:35.440Z",
  "updatedAt": "2014-08-03T01:51:41.567Z",
  "id": 16
}
```



### Notlar

> + Bu eylem _çoğul_ ("koleksiyon") ilişki ile ilgilidir.  _tekil_ ("model") ilişkisi kurmak istiyorsan, [update](http://sailsjs.org/#/documentation/reference/blueprint-api/Update.html)'i kullanabilirsin.
> + Yukarıdaki örnek "rest" blueprints'in etkin olduğunu ve senin projende en az bir 'Employee' bunun yanısıra `Store` modelinin `employeesOfTheMonth: {collection: 'Employee'}` ilişkisi ile ilişkilendiğini varsayar.  Ayrıca en az bir boş `PurchaseController` ve  `EmployeeController` 'a ihtiyacınız olacak.  Bu şekilde hızlıca oluşturabilirsin:
>
>   ```shell
>   $ sails new foo
>   $ cd foo
>   $ sails generate api purchase
>   $ sails generate api employee
>   ```
>
> ...sonra `api/models/Store.js` 'i düzelterek.

<docmeta name="uniqueID" value="Remove2294521">
<docmeta name="displayName" value="remove from">
