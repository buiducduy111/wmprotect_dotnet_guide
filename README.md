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

Một số thuộc tính ngoại lệ, sẽ không bị rename

```javascript
class Profile 
{
     public string Selected {get;set;}
     public string Name {get;set;}
}
```

Nếu sử dụng WPF, có binding XAML, sẽ cần binding qua code thủ công theo các cột
```javascript

// Lấy ra các thuộc tính của Profile (đã được rename), sau đó truy xuất theo thứ tự đã khai báo của property
List<string> propertiesName = typeof(Profile).GetProperties().Select(p => p.Name).ToList();

colName.Binding = new Binding(propertiesName[2]);
colProfilePath.Binding = new Binding(propertiesName[3]);
colBrowserType.Binding = new Binding(propertiesName[4]);
```
