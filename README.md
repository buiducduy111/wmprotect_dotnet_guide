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
