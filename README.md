<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registrasi Anggota Perpustakaan</title>
    <link rel="stylesheet" href="style.css">
    <script>
        function simpanData(event) {
            event.preventDefault(); // Mencegah halaman refresh

            let nama = document.getElementById("nama").value;
            let email = document.getElementById("email").value;
            let telepon = document.getElementById("telepon").value;
            let alamat = document.getElementById("alamat").value;
            let gender = document.querySelector('input[name="gender"]:checked').value;
            let tanggalLahir = document.getElementById("tanggalLahir").value;
            let password = document.getElementById("password").value;
            let ulangiPassword = document.getElementById("ulangiPassword").value;

            if (password !== ulangiPassword) {
                alert("Password tidak cocok!");
                return;
            }

            let anggota = JSON.parse(localStorage.getItem("anggota")) || [];
            anggota.push({ nama, email, telepon, alamat, gender, tanggalLahir });

            localStorage.setItem("anggota", JSON.stringify(anggota));

            window.location.href = "anggota.html"; // Arahkan ke halaman anggota.html
        }
    </script>
</head>
<body>
    <h2>Registrasi Anggota Perpustakaan</h2>
    <form onsubmit="simpanData(event)">
        <label for="nama">Nama Lengkap:</label>
        <input type="text" id="nama" name="nama" required>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>

        <label for="telepon">Nomor Telepon:</label>
        <input type="number" id="telepon" name="telepon" required>

        <label for="alamat">Alamat:</label>
        <textarea id="alamat" name="alamat" required></textarea>

        <label>Jenis Kelamin:</label>
        <div class="gender-container">
            <input type="radio" id="laki" name="gender" value="Laki-laki" required>
            <label for="laki">Laki-laki</label>

            <input type="radio" id="perempuan" name="gender" value="Perempuan">
            <label for="perempuan">Perempuan</label>
        </div>

        <label for="tanggalLahir">Tanggal Lahir:</label>
        <input type="date" id="tanggalLahir" name="tanggalLahir" required>

        <label for="password">Buat Password:</label>
        <input type="password" id="password" name="password" required>

        <label for="ulangiPassword">Ulangi Password:</label>
        <input type="password" id="ulangiPassword" name="ulangiPassword" required>

        <button type="submit">Daftar</button>
    </form>
</body>
</html>
