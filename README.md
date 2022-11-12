# Hướng dẫn code cùng VMProtect
[Download](https://vmpsoft.com/products/vmprotect/)

## Các chú ý:
Tất cả các thuộc tính là cột của Database cần khai báo tên Column (do thuộc tính sẽ bị rename không map được), thuộc tính nào làm khóa chính cần khai báo [Key]

```javascript
[Key]
[Column('Id')]
public int Id {get;set;}
```

Tất cả các thuộc tính là Property để parse json cần khai báo JsonProperty

```javascript
[JsonProperty("Id")]
public int Id {get;set;}
```

Nếu sử dụng EntityFramework, rename sẽ không hoạt động, cần code sang project riêng và không protect phần này

Cố gắng không gọi hàm trong tham số

```javascript
hello(sum(1,2).ToString())
```

->

```javascript
int sum = sum(1,2);
hello(sum.ToString());
```

Khai báo dynamic

```javascript
// Lỗi
var obj = new
{
    id = "123"
}

// OK
dynamic obj = new ExpandoObject();
obj.id = "123";
```

Nếu sử dụng WPF, có binding XAML, khi property bị change name sẽ gây lỗi, cần tạo project dll mới copy các UserControl có Property ra. Khi gọi namespace, thêm assmbly là tên thư viện
```
xmlns:Inputs="clr-namespace:GPMLogin.Views.Components.Inputs;assembly=GPMLogin.UI"
```

## Lỗi gây ra do thư viện
### Selenium.WebDriver
VMProtect sẽ lỗi "at <Module>..cctor()" (xem tại Event viewer) nếu cài Selenium 4.6.x (bản sử dụng selenium-manager).
    
- Cách 1: Cài xuống phiên bản thấp hơn
- Cách 2: Trên VMProtect, vào <Namespace>.App -> phương thức instance void <Namespace>.App::.ctor , chuyển chế độ Compilation Type = Virtualization
