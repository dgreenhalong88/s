<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Báo Giá Kính</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,sans-serif;
}

body{
    background:#f3f5f7;
    padding:15px;
}

.container{
    max-width:500px;
    margin:auto;
}

.card{
    background:#fff;
    border-radius:18px;
    padding:20px;
    box-shadow:0 5px 15px rgba(0,0,0,0.08);
}

h1{
    text-align:center;
    color:#0d6efd;
    margin-bottom:20px;
}

label{
    display:block;
    margin-top:15px;
    margin-bottom:5px;
    font-weight:600;
}

input,select{
    width:100%;
    padding:12px;
    border:1px solid #ddd;
    border-radius:10px;
    font-size:16px;
}

button{
    width:100%;
    margin-top:20px;
    padding:15px;
    border:none;
    border-radius:12px;
    background:#0d6efd;
    color:white;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
}

button:hover{
    opacity:.9;
}

.result{
    margin-top:20px;
    background:#eef7ff;
    border-radius:12px;
    padding:15px;
}

.row{
    display:flex;
    justify-content:space-between;
    margin-bottom:10px;
}

.total{
    margin-top:10px;
    padding-top:10px;
    border-top:2px dashed #ccc;
    font-size:24px;
    font-weight:bold;
    color:#e63946;
    text-align:center;
}
</style>
</head>

<body>

<div class="container">

<div class="card">

<h1>🪟 BÁO GIÁ KÍNH</h1>

<label>Chiều rộng (mm)</label>
<input type="number" id="width" placeholder="Ví dụ 1000">

<label>Chiều cao (mm)</label>
<input type="number" id="height" placeholder="Ví dụ 2000">

<label>Loại kính</label>
<select id="glassType">
<option value="300000">Kính 4mm</option>
<option value="350000">Kính 5mm</option>
<option value="700000">Kính 10mm</option>
<option value="850000">Kính 12mm</option>
</select>

<label>Mài cạnh</label>
<select id="polish">
<option value="0">Không mài cạnh</option>
<option value="50000">Có mài cạnh</option>
</select>

<button onclick="calculate()">
TÍNH BÁO GIÁ
</button>

<div class="result">

<div class="row">
<span>Diện tích:</span>
<span id="area">0 m²</span>
</div>

<div class="row">
<span>Đơn giá kính:</span>
<span id="price">0 đ</span>
</div>

<div class="row">
<span>Mài cạnh:</span>
<span id="edge">0 đ</span>
</div>

<div class="total" id="total">
0 đ
</div>

</div>

</div>

</div>

<script>

function calculate(){

let w=parseFloat(document.getElementById('width').value)||0;
let h=parseFloat(document.getElementById('height').value)||0;

if(w<=0||h<=0){
alert("Vui lòng nhập kích thước");
return;
}

let area=(w*h)/1000000;

let glass=document.getElementById('glassType');
let glassPrice=parseFloat(glass.value);

let polish=document.getElementById('polish');
let polishPrice=parseFloat(polish.value);

let total=area*(glassPrice+polishPrice);

document.getElementById('area').innerHTML=
area.toFixed(2)+" m²";

document.getElementById('price').innerHTML=
glassPrice.toLocaleString('vi-VN')+" đ/m²";

document.getElementById('edge').innerHTML=
polishPrice.toLocaleString('vi-VN')+" đ/m²";

document.getElementById('total').innerHTML=
"💰 "+total.toLocaleString('vi-VN')+" đ";

}

</script>

</body>
</html>