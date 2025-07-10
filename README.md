<?php
include "phpqrcode/qrlib.php"; // pastikan folder phpqrcode ada

// Pesan untuk dijadikan QR
$pesan = "Aku pernah melihat ibuku menangis karena ulahku, 
namun ia tak pernah membenci anaknya, 
melainkan selalu memaafkannya. 
Maaf, Bu... jika aku belum bisa membuatmu bahagia.";

// Buat output QR langsung ke browser sebagai data URI (base64)
ob_start();
QRcode::png($pesan, null, QR_ECLEVEL_H, 6);
$imageData = ob_get_contents();
ob_end_clean();

// Encode jadi base64
$base64 = base64_encode($imageData);
?>

<!DOCTYPE html>
<html>

<head>
    <title>QR Code untuk Ibu</title>
    <style>
        body {
            background-color: #fdf2f8;
            font-family: Arial, sans-serif;
            text-align: center;
            padding-top: 50px;
        }

        img {
            margin-top: 20px;
            border: 4px solid #fbb6ce;
            border-radius: 10px;
        }
    </style>
</head>

<body>
    <h2>QR Code dari Pesan untuk Ibu</h2>
    <img src="data:image/png;base64,<?= $base64 ?>" alt="QR Code">
    <p>Scan untuk membaca pesan haru ini</p>
</body>

</html>
