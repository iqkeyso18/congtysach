<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Công ty Sách ABC - Nhà phân phối sách chính hãng, đa dạng thể loại, cập nhật nhanh nhất. Mua sách online, giá ưu đãi, giao hàng tận nơi.">
  <meta name="keywords" content="sách, mua sách online, sách hay, công ty sách, sách ABC">
  <meta name="author" content="Công ty Sách ABC">
  <title>Công ty Sách ABC - Website Quản Lý & Giới Thiệu Sách</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      background: #f6f9fc;
      color: #333;
      scroll-behavior: smooth;
    }
    header {
      background: linear-gradient(135deg, #007bff, #00c6ff);
      color: white;
      padding: 20px;
      text-align: center;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
      position: sticky;
      top: 0;
      z-index: 10;
    }
    nav a {
      color: white;
      margin: 0 15px;
      text-decoration: none;
      font-weight: bold;
      transition: color 0.3s;
    }
    nav a:hover {
      color: #ffe100;
    }
    .hero {
      background: url('https://images.unsplash.com/photo-1524995997946-a1c2e315a42f') center/cover no-repeat;
      color: white;
      text-align: center;
      padding: 120px 20px;
      animation: fadeIn 2s ease-in;
    }
    .hero h1 {
      font-size: 3em;
      text-shadow: 2px 2px 6px rgba(0,0,0,0.6);
    }
    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(-20px);}
      to {opacity: 1; transform: translateY(0);}
    }
    .container {
      padding: 30px;
      max-width: 1200px;
      margin: auto;
    }
    .book-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 25px;
    }
    .book-card {
      background: white;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      overflow: hidden;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .book-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }
    .book-card img {
      width: 100%;
      height: 300px;
      object-fit: cover;
    }
    .book-info {
      padding: 20px;
    }
    .book-info h3 {
      margin: 0;
      color: #007bff;
    }
    .search-bar {
      display: flex;
      justify-content: center;
      margin-bottom: 20px;
    }
    .search-bar input {
      width: 60%;
      padding: 10px;
      border-radius: 30px;
      border: 1px solid #ccc;
      outline: none;
      transition: box-shadow 0.3s;
    }
    .search-bar input:focus {
      box-shadow: 0 0 8px #007bff;
    }
    footer {
      background: #007bff;
      color: white;
      text-align: center;
      padding: 15px 0;
      margin-top: 40px;
    }
    .admin-section {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      animation: fadeIn 1.5s ease;
    }
    button {
      background: linear-gradient(135deg, #007bff, #00c6ff);
      border: none;
      color: white;
      padding: 10px 20px;
      border-radius: 25px;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background: linear-gradient(135deg, #0056b3, #0091d1);
    }
  </style>
</head>
<body>
  <header>
    <h1>CÔNG TY BÁN SÁCH TRẦN HỮU LUÂN</h1>
    <nav>
      <a href="#home">Trang Chủ</a>
      <a href="#Sach">Sách hay</a>
      <a href="#admin">Admin</a>
    </nav>
  </header>
  <section class="hero" id="home">
    <h1>Khám phá kho tàng tri thức cùng Sách ABC</h1>
    <p>Đọc để trưởng thành - Chia sẻ để lan tỏa tri thức</p>
    <button onclick="window.location='#books'">Xem ngay</button>
  </section>

  <div class="container" id="books">
    <h2>Danh sách Sách</h2>
    <div class="search-bar">
      <input type="text" id="searchInput" placeholder="Tìm theo tên, tác giả hoặc mô tả..." onkeyup="searchBooks()">
    </div>
    <div id="bookList" class="book-grid"></div>
  </div>

  <div class="container" id="admin">
    <div class="admin-section">
      <h2>Trang Quản Trị Sách (Admin)</h2>
      <div id="adminLogin">
        <input type="password" id="adminPass" placeholder="Nhập mật khẩu admin">
        <button onclick="loginAdmin()">Đăng nhập</button>
      </div>
      <div id="adminPanel" style="display:none">
        <h3>Thêm / Cập nhật Sách</h3>
        <input id="bookId" placeholder="Mã sách"/><br><br>
        <input id="bookName" placeholder="Tên sách"/><br><br>
        <input id="bookAuthor" placeholder="Tác giả"/><br><br>
        <textarea id="bookDesc" placeholder="Tóm tắt nội dung"></textarea><br><br>
        <input id="bookYear" type="number" placeholder="Năm xuất bản"/><br><br>
        <input id="bookPrice" type="number" placeholder="Giá bán"/><br><br>
        <input id="bookImg" placeholder="URL hình ảnh"/><br><br>
        <button onclick="addOrUpdateBook()">Thêm/Cập nhật</button>
        <button onclick="clearForm()">Làm mới</button>
        <hr>
        <h3>Danh sách Quản lý</h3>
        <table id="adminTable" border="1" width="100%" style="border-collapse:collapse;text-align:center">
          <thead><tr><th>Mã</th><th>Tên</th><th>Tác giả</th><th>Giá</th><th>Năm</th><th>Thao tác</th></tr></thead>
          <tbody></tbody>
        </table>
      </div>
    </div>
  </div>

  <footer>
    <p>© 2025 Công ty Sách ABC - Website chuẩn SEO | Liên hệ: info@sachabc.vn</p>
  </footer>

  <script>
    class Book {
      constructor(id, name, author, desc, price, year, img){
        this.id=id;this.name=name;this.author=author;this.desc=desc;this.price=price;this.year=year;this.img=img;
      }
    }
    class BookManager {
      constructor(){this.books=JSON.parse(localStorage.getItem('books')||'[]');}
      save(){localStorage.setItem('books',JSON.stringify(this.books));}
      addOrUpdate(book){const idx=this.books.findIndex(b=>b.id===book.id);if(idx>=0)this.books[idx]=book;else this.books.push(book);this.save();}
      delete(id){this.books=this.books.filter(b=>b.id!==id);this.save();}
      search(key){key=key.toLowerCase();return this.books.filter(b=>b.name.toLowerCase().includes(key)||b.author.toLowerCase().includes(key)||b.desc.toLowerCase().includes(key));}
    }

    const manager=new BookManager();

    function renderBooks(list){
      const container=document.getElementById('bookList');
      container.innerHTML='';
      list.forEach(b=>{
        container.innerHTML+=`<div class='book-card'>
          <img src='${b.img}' alt='${b.name}'>
          <div class='book-info'>
            <h3>${b.name}</h3>
            <p><b>Tác giả:</b> ${b.author}</p>
            <p><b>Năm:</b> ${b.year}</p>
            <p>${b.desc.substring(0,100)}...</p>
            <p><b>Giá:</b> ${b.price.toLocaleString()}₫</p>
          </div>
        </div>`;
      });
    }

    function renderAdmin(){
      const tbody=document.querySelector('#adminTable tbody');
      tbody.innerHTML='';
      manager.books.forEach(b=>{
        tbody.innerHTML+=`<tr><td>${b.id}</td><td>${b.name}</td><td>${b.author}</td><td>${b.price}</td><td>${b.year}</td><td><button onclick="editBook('${b.id}')">Sửa</button> <button onclick="deleteBook('${b.id}')">Xóa</button></td></tr>`;
      });
    }

    function addOrUpdateBook(){
      const b=new Book(bookId.value, bookName.value, bookAuthor.value, bookDesc.value, Number(bookPrice.value), Number(bookYear.value), bookImg.value||'https://images.unsplash.com/photo-1524995997946-a1c2e315a42f');
      manager.addOrUpdate(b);renderBooks(manager.books);renderAdmin();clearForm();alert('Đã lưu sách!');
    }
    function deleteBook(id){if(confirm('Xóa sách này?')){manager.delete(id);renderBooks(manager.books);renderAdmin();}}
    function editBook(id){const b=manager.books.find(b=>b.id===id);bookId.value=b.id;bookName.value=b.name;bookAuthor.value=b.author;bookDesc.value=b.desc;bookPrice.value=b.price;bookYear.value=b.year;bookImg.value=b.img;}
    function clearForm(){bookId.value='';bookName.value='';bookAuthor.value='';bookDesc.value='';bookPrice.value='';bookYear.value='';bookImg.value='';}
    function searchBooks(){const key=document.getElementById('searchInput').value;renderBooks(manager.search(key));}

    function loginAdmin(){const pass=document.getElementById('adminPass').value;if(pass==='admin123'){document.getElementById('adminLogin').style.display='none';document.getElementById('adminPanel').style.display='block';renderAdmin();}else alert('Sai mật khẩu!');}

    if(manager.books.length===0){manager.books=[
      new Book('S001','Đắc Nhân Tâm','Dale Carnegie','Cuốn sách kinh điển về nghệ thuật giao tiếp.',79000,2021,'https://images.unsplash.com/photo-1512820790803-83ca734da794'),
      new Book('S002','Tuổi Trẻ Đáng Giá Bao Nhiêu','Rosie Nguyễn','Khám phá bản thân, sống có ý nghĩa.',88000,2020,'https://images.unsplash.com/photo-1553729459-efe14ef6055d'),
      new Book('S003','Nhà Giả Kim','Paulo Coelho','Câu chuyện truyền cảm hứng về hành trình theo đuổi ước mơ.',99000,2022,'https://images.unsplash.com/photo-1495446815901-a7297e633e8d')
    ];manager.save();}

    renderBooks(manager.books);
  </script>
</body>
</html>
