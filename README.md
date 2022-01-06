# Hướng dẫn code cùng VMProtect

## Các chú ý:
Tất cả các thuộc tính là cột của Database cần khai báo tên Column (do thuộc tính sẽ bị rename không map được), thuộc tính nào làm khóa chính cần khai báo [Key]

```javascript
[Key]
[Column('Id')]
public int Id {get;set;}
```

2. Tất cả các thuộc tính là Property để parse json cần khai báo JsonProperty
3. 
```javascript
[JsonProperty("Id")]
public int Id {get;set;}
```

3. Nếu sử dụng EntityFramework, rename sẽ không hoạt động, cần code sang project riêng và không protect phần này

4. Cố gắng không gọi hàm trong tham số

```javascript
hello(sum(1,2).ToString())
```
