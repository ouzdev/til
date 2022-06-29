Sunucu üzerinden birden fazla istemciye hizmet verecek şekilde tasarlanmış uygulama mimarilerinde her bir istek için benzersiz bir Context nesnesi üretilir.

Context üzerinde de istemci tarafında yapılan Request neticesince uygulamaya ve isteğe ait bazı bilgilere ulaşılabilir.

Context nesnesi yaşadığı sürece saklanması gereken bilgilerinde tutulduğu koleksiyon sunmaktadır.

.Net Core ile beraber HttpContext nesnesine erişmek için IHttpContextAccessor interface'i kullanılmaktadır. Bu interface Singleton şekilde Root Scope'da yaşayacak şekilde instance oluşturulmaktadır. DI container'da tanımlama yaptıktan sonra istenilen yerde interface inject edilerek kullanılabilmektedir.

```
public class ContactModel : PageModel
{
   public string Message { get; set; }

   public void OnGet()
   {
      Message = this.HttpContext.Items["Message"].ToString();
   }

   private readonly IHttpContextAccessor HttpContextAccessor;

   public ContactModel(IHttpContextAccessor httpContextAccessor)
   {
        this.HttpContextAccessor = httpContextAccessor;

        this.HttpContextAccessor.HttpContext.Items["Message"] = "İletişim Sayfası";
   }
}
```

Yukarıda ki kod bloğunda olduğu gibi inject edilebilmektedir.






