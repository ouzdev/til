Dependency Injection, geliştirilen projede loosely coupled code geliştirmek için kullanılan ve içerisinde Inversion of Control ve Dependency Inversion prensiplerini barındıran bir desing pattern'dir.
## Neden Dependency Injection Kullanırız ?
Amaç olarak kod içinde bağımlılıkları azaltmak veya bağımlılıkları tersine çevirmekte diyebiliriz. Gelişime açık esnek yapılar oluşturmak ie birlikte ve test edilebilir kod yazmaktır. Bir başka deyişle direk concrate class'lar ile çalışmak yerine interface'ler ile çalışarak bu interfacelerin arkasında çalışacak concrate class instancelerinin life time ile ilgili süreçleri yönettiğimiz bir yapıdır.

### Yararları Nelerdir ?
* Modüler ve Componentler arası bağlılığı azaltır.
* Bakım ve geliştirmelerde kolaylık sağlar.
* Test edilebilirliği arttırır.
* Okunabilirliği arttırır.

## Servisler Nasıl Register Edilir ?

Servisler Startup.cs içerisinde ConfigureServices methodu ile alınan services parametresi ile register edilir. Services parametre tipi IServiceCollection'dır. Servisler IServiceCollection vasıtasıyla register olur. Servisleri resolve ederken IServisProvider nesnesi vasıtasıyla olmaktadır.

### Service Life-Time

* **Singleton**: Uygulama ömrü boyunca Root Space'de tek bir instance oluşturulur ve yeni bir instance oluşturulmaz.

* **Scoped**: Her bir requeste özgü service scope oluşturulur ve bu scope içerisinde sadece bir instance oluşturulur. Request sona ereseye kadar tanımlanan instance yaşamına devam eder.

* **Transient**: Her requestte IoC  yeni bir instance oluşturulur.

### Register Edilen Servisler Ne Zaman Trigger Edilir ? 

Burada ki öenmli olan nokta bir request başlatıldığında ilgili entpoint in dahil olduğu controllerda dependency injection ile inject edilmiş servis interface i genellikle ilgili controller sınıfının yapıcı(cunstructor) metodunda bulunur. Burada inject edilen tüm servisler service lifetime tanımlamalarına göre instanceleri oluşturulur.