# Hướng dẫn code cùng VMProtect

## Các chú ý:
1. Tất cả các thuộc tính là cột của Database cần khai báo tên Column (do thuộc tính sẽ bị rename không map được), thuộc tính nào làm khóa chính cần khai báo [Key]

[Key]
[Column('Id')]
public int Id {get;set;}

2. Tất cả các thuộc tính là Property để parse json cần khai báo JsonProperty

[JsonProperty("Id")]
public int Id {get;set;}
