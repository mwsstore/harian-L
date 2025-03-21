
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>

.promo {
    background: linear-gradient(to bottom, #169c7a, #0069d9);
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(10, 186, 217, 0.1);
    margin-bottom: 20px;
}

.promo H5 {
    color: #f7f7f7;
    font-size: 15px;
    margin-bottom: 8px;
}

.promo H4 {
    color: #f7f7f7;
    font-size: 20px;
    margin-bottom: 9px;
}
.PROMO h1 {
    color: #62e034;
    font-size: 24px;
    margin-bottom: 10px;
}
.promo .harga {
    color: #ffff00; /* Warna kuning */
    font-size: 26px;
    font-weight: bold;
    margin-bottom: 10px;
}

.promo ul {
    list-style: none;
    padding: 0;
    margin: 0;
}

.promo ul li {
    color: #f7f7f7;
    margin-bottom: 15px;
    font-size: 18px;
}

.promo button {
    background-color: #007bff;
    color: #f7f7f7;
    border: none;
    padding: 15px 30px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 18px;
}

.promo button:hover {
    background-color: #0069d9;
}

button {
    background: linear-gradient(to bottom, #34C759, #2ECC71);
    color: #fff;
    border: none;
    padding: 15px 30px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 18px;
}

button:hover {
    background: linear-gradient(to bottom, #2ECC71, #34C759);
}



.garansi {
    font-size: 18px;
    color: #e20d8a;
    margin-top: 20px;
}

.garansi span {
    font-weight: bold;
}


    </style>
</head>

<body>
<div class="promo">
    <H4>🔰DESKRIPSI ANGGOTA L🔰 </H4>
    <ul><BR>
        <h1>Area 1 = 8 GB</h1>
        <H1>Area 2 = 10 GB</H1>
        <H1>Area 3 = 15 GB</H1>
        <H1>Area 4 = 25 GB</H1>
    </ul>
    <BR>
    <H5>🔰Anggota L 3 hari🔰 🏷Rp.6rb</H5>
    <H5>🔰Anggota L 5 hari🔰 🏷Rp.8rb</H5>
    <H5>🔰Anggota L 7 hari🔰 🏷Rp.10rb</H5>
    <H5>🔰Anggota L 9 hari🔰 🏷Rp.13rb</H5>
    <H5>🔰Anggota L 11 hari🔰 🏷Rp.15rb</H5>
    <H5>🔰Anggota L 13 hari🔰 🏷Rp.17rb</H5>
    <H5>🔰Anggota L 15 hari🔰 🏷Rp.19rb</H5>
    <H5>🔰Anggota L 17 hari🔰 🏷Rp.21rb</H5>
    <H5>🔰Anggota L 19 hari🔰 🏷Rp.23rb</H5><BR><BR>
    <ul id="stok-anggota-l-list">
        <!-- Stok akan ditampilkan di sini -->
    </ul><BR><BR>
    <button id="cek-stok-anggota-l-btn">Cek Stok</button>
</div>
<script>
    const stokAnggotaLList = document.getElementById('stok-anggota-l-list');
const cekStokAnggotaLBtn = document.getElementById('cek-stok-anggota-l-btn');

cekStokAnggotaLBtn.addEventListener('click', async () => {
try {
    const response = await fetch('https://panel.khfy-store.com/api/api-xl-v7/cek_stock_akrab');
    const data = await response.json();

    const anggotaLStok = data.message.match(/Anggota L (\d+) hari : (\d+) tersedia/g);
    stokAnggotaLList.innerHTML = '';
    anggotaLStok.forEach((stok) => {
        const listItem = document.createElement('li');
        listItem.innerText = stok;
        stokAnggotaLList.appendChild(listItem);
    });
} catch (error) {
    console.error(error);
}
});
const stokSuperMiniList = document.getElementById('stok-super-mini-list');
const cekStokSuperMiniBtn = document.getElementById('cek-stok-super-mini-btn');
const stokExtraMiniList = document.getElementById('stok-extra-mini-list');
const cekStokExtraMiniBtn = document.getElementById('cek-stok-extra-mini-btn');
const stokSuperBigList = document.getElementById('stok-super-big-list');
const cekStokSuperBigBtn = document.getElementById('cek-stok-super-big-btn');

cekStokSuperBigBtn.addEventListener('click', async () => {
try {
    const response = await fetch('https://panel.khfy-store.com/api/api-xl-v7/cek_stock_akrab');
    const data = await response.json();

    const superBigStok = data.message.match(/SuperBig PROMO : (\d+) tersedia/);
    if (superBigStok) {
        stokSuperBigList.innerHTML = '';
        const listItem = document.createElement('li');
        listItem.innerText = `SuperBig PROMO: ${superBigStok[1]} tersedia`;
        stokSuperBigList.appendChild(listItem);
    } else {
        stokSuperBigList.innerHTML = '';
        const listItem = document.createElement('li');
        listItem.innerText = 'Tidak ada stok SuperBig PROMO';
        stokSuperBigList.appendChild(listItem);
    }
} catch (error) {
    console.error(error);
}
});
cekStokSuperMiniBtn.addEventListener('click', async () => {
    try {
        const response = await fetch('https://panel.khfy-store.com/api/api-xl-v7/cek_stock_akrab');
        const data = await response.json();

        const superMiniStok = data.message.match(/SuperMini PROMO : (\d+) tersedia/);
        if (superMiniStok) {
            stokSuperMiniList.innerHTML = '';
            const listItem = document.createElement('li');
            listItem.innerText = `SuperMini PROMO: ${superMiniStok[1]} tersedia`;
            stokSuperMiniList.appendChild(listItem);
        } else {
            stokSuperMiniList.innerHTML = '';
            const listItem = document.createElement('li');
            listItem.innerText = 'Tidak ada stok SuperMini PROMO';
            stokSuperMiniList.appendChild(listItem);
        }
    } catch (error) {
        console.error(error);
    }
});

cekStokExtraMiniBtn.addEventListener('click', async () => {
    try {
        const response = await fetch('https://panel.khfy-store.com/api/api-xl-v7/cek_stock_akrab');
        const data = await response.json();

        const extraMiniStok = data.message.match(/ExtraMini PROMO : (\d+) tersedia/);
        if (extraMiniStok) {
            stokExtraMiniList.innerHTML = '';
            const listItem = document.createElement('li');
            listItem.innerText = `ExtraMini PROMO: ${extraMiniStok[1]} tersedia`;
            stokExtraMiniList.appendChild(listItem);
        } else {
            stokExtraMiniList.innerHTML = '';
            const listItem = document.createElement('li');
            listItem.innerText = 'Tidak ada stok ExtraMini PROMO';
            stokExtraMiniList.appendChild(listItem);
        }
    } catch (error) {
        console.error(error);
    }
});
</script>


<a href="https://wa.me/6287748842242" target="_blank" class="wa-button">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6b/WhatsApp.svg/1200px-WhatsApp.svg.png" alt="Tombol WA">
</a>

<style>
.wa-button {
position: fixed;
bottom: 20px;
right: 20px;
z-index: 1000;
}

.wa-button img {
width: 50px;
height: 50px;
border-radius: 50%;
}
</style>
