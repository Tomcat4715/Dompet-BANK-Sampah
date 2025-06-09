<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Bank Sampah ARAS - Dompet Digital</title>
    <style>
        /* === KODE CSS LENGKAP - TIDAK ADA PERUBAHAN, SUDAH SEMPURNA === */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: linear-gradient(135deg, #f0f4f8 0%, #d9e2ec 100%); color: #333; min-height: 100vh; overflow-x: hidden; }
        .app-container { max-width: 414px; margin: 0 auto; background: #f8f9fa; min-height: 100vh; box-shadow: 0 0 20px rgba(0,0,0,0.1); position: relative; }
        .header { background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%); color: white; padding: 25px 20px 30px; text-align: center; position: relative; overflow: hidden; border-bottom-left-radius: 20px; border-bottom-right-radius: 20px;}
        .header::before { content: ''; position: absolute; top: -50%; right: -20%; width: 100px; height: 100px; background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%); border-radius: 50%; animation: float 6s ease-in-out infinite; }
        @keyframes float { 0%, 100% { transform: translateY(0px) rotate(0deg); } 50% { transform: translateY(-20px) rotate(180deg); } }
        .logo-container { display: flex; align-items: center; justify-content: center; margin-bottom: 10px; }
        .logo-icon { font-size: 32px; margin-right: 10px; }
        .logo-text { font-size: 24px; font-weight: bold; }
        .bank-name { font-size: 16px; opacity: 0.9; margin-bottom: 5px; }
        .location { font-size: 12px; opacity: 0.8; }
        .user-card { background: linear-gradient(135deg, #3498db 0%, #2980b9 100%); margin: -15px 20px 20px; padding: 20px; border-radius: 20px; color: white; box-shadow: 0 10px 30px rgba(52, 152, 219, 0.3); position: relative; overflow: hidden; }
        .user-card::before { content: '♻️'; position: absolute; top: 10px; right: 15px; font-size: 40px; opacity: 0.2; }
        .user-greeting { font-size: 14px; opacity: 0.9; margin-bottom: 5px; }
        .user-name { font-size: 20px; font-weight: bold; margin-bottom: 15px; }
        .user-stats { display: flex; justify-content: space-between; align-items: center; }
        .stat-item { text-align: center; }
        .stat-value { font-size: 18px; font-weight: bold; }
        .stat-label { font-size: 10px; opacity: 0.8; }
        .balance-section { padding: 0 20px; margin-bottom: 25px; }
        .balance-card { background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%); padding: 25px; border-radius: 20px; color: white; text-align: center; box-shadow: 0 10px 30px rgba(231, 76, 60, 0.3); position: relative; overflow: hidden; }
        .balance-card::before { content: '💰'; position: absolute; top: -10px; right: -10px; font-size: 60px; opacity: 0.1; transform: rotate(15deg); }
        .balance-label { font-size: 14px; opacity: 0.9; margin-bottom: 8px; }
        .balance-amount { font-size: 32px; font-weight: bold; margin-bottom: 15px; }
        .balance-actions { display: flex; gap: 10px; }
        .balance-btn { flex: 1; background: rgba(255,255,255,0.2); border: none; color: white; padding: 10px; border-radius: 10px; font-size: 12px; cursor: pointer; transition: all 0.3s ease; backdrop-filter: blur(10px); }
        .balance-btn:hover { background: rgba(255,255,255,0.3); transform: translateY(-2px); }
        .features-section { padding: 0 20px; margin-bottom: 25px; }
        .section-title { font-size: 18px; font-weight: bold; color: #2c3e50; margin-bottom: 15px; display: flex; align-items: center; }
        .section-title::before { content: '🌱'; margin-right: 8px; }
        .features-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 15px; margin-bottom: 20px; }
        .feature-item { background: white; border-radius: 15px; padding: 20px 10px; text-align: center; box-shadow: 0 5px 15px rgba(0,0,0,0.08); cursor: pointer; transition: all 0.3s ease; border: 2px solid transparent; }
        .feature-item:hover { transform: translateY(-5px); box-shadow: 0 10px 25px rgba(0,0,0,0.15); border-color: #2ecc71; }
        .feature-icon { font-size: 28px; margin-bottom: 8px; display: block; }
        .feature-text { font-size: 12px; color: #2c3e50; font-weight: 600; }
        .waste-calculator { background: linear-gradient(135deg, #f39c12 0%, #e67e22 100%); margin: 0 20px 20px; padding: 20px; border-radius: 15px; color: white; position: relative; overflow: hidden; }
        .waste-calculator::before { content: '⚖️'; position: absolute; top: 10px; right: 15px; font-size: 35px; opacity: 0.3; }
        .calculator-title { font-size: 16px; font-weight: bold; margin-bottom: 15px; }
        .calculator-row { display: flex; align-items: center; margin-bottom: 10px; }
        .calculator-input { flex: 1; background: rgba(255,255,255,0.2); border: none; color: white; padding: 8px 12px; border-radius: 8px; margin-right: 10px; font-size: 14px; }
        .calculator-input::placeholder { color: rgba(255,255,255,0.7); }
        .calculator-btn { background: rgba(255,255,255,0.2); border: none; color: white; padding: 8px 15px; border-radius: 8px; cursor: pointer; font-size: 12px; transition: all 0.3s ease; }
        .calculator-btn:hover { background: rgba(255,255,255,0.3); }
        .calculator-result { background: rgba(255,255,255,0.1); padding: 10px; border-radius: 8px; margin-top: 10px; text-align: center; font-weight: bold; }
        .transactions-section { padding: 0 20px; margin-bottom: 100px; }
        .transaction-item { background: white; border-radius: 12px; padding: 15px; margin-bottom: 10px; box-shadow: 0 3px 10px rgba(0,0,0,0.05); display: flex; align-items: center; border-left: 4px solid; transition: all 0.3s ease; }
        .transaction-item:hover { transform: translateX(5px); box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .transaction-item.setor { border-left-color: #27ae60; } .transaction-item.tarik { border-left-color: #e74c3c; } .transaction-item.reward { border-left-color: #f39c12; }
        .transaction-icon { width: 45px; height: 45px; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin-right: 15px; font-size: 20px; color: white; }
        .transaction-icon.setor { background: linear-gradient(135deg, #27ae60, #2ecc71); } .transaction-icon.tarik { background: linear-gradient(135deg, #e74c3c, #c0392b); } .transaction-icon.reward { background: linear-gradient(135deg, #f39c12, #e67e22); }
        .transaction-info { flex: 1; }
        .transaction-title { font-weight: 600; color: #2c3e50; margin-bottom: 3px; }
        .transaction-detail { font-size: 12px; color: #7f8c8d; margin-bottom: 2px; }
        .transaction-date { font-size: 10px; color: #95a5a6; }
        .transaction-amount { font-weight: bold; font-size: 14px; text-align: right; }
        .transaction-amount.setor { color: #27ae60; } .transaction-amount.tarik { color: #e74c3c; } .transaction-amount.reward { color: #f39c12; }
        .floating-btn { position: fixed; bottom: 80px; right: 20px; width: 60px; height: 60px; background: linear-gradient(135deg, #2ecc71, #27ae60); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-size: 24px; cursor: pointer; box-shadow: 0 10px 25px rgba(46, 204, 113, 0.4); transition: all 0.3s ease; animation: pulse 2s infinite; z-index: 100; }
        @keyframes pulse { 0% { box-shadow: 0 10px 25px rgba(46, 204, 113, 0.4); } 50% { box-shadow: 0 15px 35px rgba(46, 204, 113, 0.6); } 100% { box-shadow: 0 10px 25px rgba(46, 204, 113, 0.4); } }
        .floating-btn:hover { transform: scale(1.1); }
        .bottom-nav { position: fixed; bottom: 0; left: 50%; transform: translateX(-50%); width: 100%; max-width: 414px; background: white; border-top: 1px solid #e0e0e0; display: flex; padding: 10px 0; box-shadow: 0 -5px 15px rgba(0,0,0,0.1); z-index: 99; }
        .nav-item { flex: 1; text-align: center; padding: 10px; cursor: pointer; transition: all 0.3s ease; color: #7f8c8d; }
        .nav-item.active { color: #2ecc71; }
        .nav-icon { font-size: 20px; margin-bottom: 3px; }
        .nav-text { font-size: 10px; font-weight: 500; }
        .eco-tips { background: linear-gradient(135deg, #16a085, #1abc9c); margin: 0 20px 20px; padding: 15px; border-radius: 12px; color: white; position: relative; overflow: hidden; }
        .eco-tips::before { content: '💡'; position: absolute; top: 10px; right: 15px; font-size: 30px; opacity: 0.3; }
        .tips-title { font-weight: bold; margin-bottom: 8px; font-size: 14px; }
        .tips-content { font-size: 12px; line-height: 1.4; opacity: 0.95; }
        .stats-overview { display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; margin: 0 20px 20px; }
        .stat-card { background: white; padding: 15px; border-radius: 12px; text-align: center; box-shadow: 0 3px 10px rgba(0,0,0,0.05); border-top: 3px solid; }
        .stat-card.plastic { border-top-color: #3498db; } .stat-card.organic { border-top-color: #27ae60; }
        .stat-number { font-size: 24px; font-weight: bold; color: #2c3e50; margin-bottom: 5px; }
        .stat-description { font-size: 12px; color: #7f8c8d; }
        /* Modal (Pop-up) Styles */
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); z-index: 1000; backdrop-filter: blur(5px); align-items: center; justify-content: center; }
        .modal-content { position: relative; background: white; padding: 30px; border-radius: 20px; width: 90%; max-width: 350px; text-align: center; box-shadow: 0 20px 40px rgba(0,0,0,0.3); animation: zoomIn 0.3s ease-out; }
        @keyframes zoomIn { from { transform: scale(0.8); opacity: 0; } to { transform: scale(1); opacity: 1; } }
        .modal-icon { font-size: 48px; margin-bottom: 15px; }
        .modal-title { font-size: 20px; font-weight: bold; margin-bottom: 10px; color: #2c3e50; }
        .modal-text { font-size: 14px; color: #666; margin-bottom: 20px; line-height: 1.5; white-space: pre-wrap; }
        .modal-btn { background: linear-gradient(135deg, #2ecc71, #27ae60); color: white; border: none; padding: 12px 30px; border-radius: 25px; font-size: 14px; font-weight: 600; cursor: pointer; transition: all 0.3s ease; }
        .modal-btn:hover { transform: translateY(-2px); box-shadow: 0 5px 15px rgba(46, 204, 113, 0.3); }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- Header -->
        <div class="header">
            <div class="logo-container"><div class="logo-icon">♻️</div><div class="logo-text">BANK SAMPAH ARAS</div></div>
            <div class="bank-name">Karangtaruna ARAS</div>
            <div class="location">Dusun Citambal</div>
        </div>

        <!-- User Card -->
        <div class="user-card">
            <div class="user-greeting">Selamat datang,</div>
            <div class="user-name">Ajis Abdul Jabar</div>
            <div class="user-stats">
                <div class="stat-item"><div class="stat-value">47</div><div class="stat-label">Hari Aktif</div></div>
                <div class="stat-item"><div class="stat-value">23kg</div><div class="stat-label">Total Sampah</div></div>
                <div class="stat-item"><div class="stat-value">⭐ 4.8</div><div class="stat-label">®™ rung's</div></div>
            </div>
        </div>

        <!-- Balance Section -->
        <div class="balance-section">
            <div class="balance-card">
                <div class="balance-label">Saldo Tabungan Sampah</div>
                <div class="balance-amount" id="balance">Rp 347.500</div>
                <!-- === TOMBOL KEUANGAN YANG SUDAH DIUBAH === -->
                <div class="balance-actions">
                    <button class="balance-btn" onclick="showTransfer()">💸 Transfer</button>
                    <button class="balance-btn" onclick="showRincianSaldo()">🧾 Rincian Saldo</button>
                    <button class="balance-btn" onclick="showIsiSaldo()">➕ Cara Isi Saldo</button>
                </div>
            </div>
        </div>

        <!-- Statistics & Tips -->
        <div class="stats-overview">
            <div class="stat-card plastic"><div class="stat-number">15.2kg</div><div class="stat-description">Sampah Plastik Bulan Ini</div></div>
            <div class="stat-card organic"><div class="stat-number">8.7kg</div><div class="stat-description">Sampah Organik Bulan Ini</div></div>
        </div>
        <div class="eco-tips">
            <div class="tips-title">💡 Tips Ramah Lingkungan Hari Ini</div>
            <div class="tips-content">Pisahkan sampah plastik dan organik sebelum disetor. Sampah yang sudah dipilah akan mendapat harga lebih tinggi!</div>
        </div>

        <!-- Features Section -->
        <div class="features-section">
            <div class="section-title">Layanan Bank Sampah</div>
            <div class="features-grid">
                <div class="feature-item" onclick="showSetor()"><div class="feature-icon">📥</div><div class="feature-text">Setor Sampah</div></div>
                <div class="feature-item" onclick="showHarga()"><div class="feature-icon">💰</div><div class="feature-text">Harga Sampah</div></div>
                <div class="feature-item" onclick="showJadwal()"><div class="feature-icon">📅</div><div class="feature-text">Jadwal Pickup</div></div>
                <div class="feature-item" onclick="showPanduan()"><div class="feature-icon">📖</div><div class="feature-text">Panduan</div></div>
                <div class="feature-item" onclick="showLeaderboard()"><div class="feature-icon">🏆</div><div class="feature-text">Leaderboard</div></div>
                <div class="feature-item" onclick="showReward()"><div class="feature-icon">🎁</div><div class="feature-text">Tukar Poin</div></div>
            </div>
        </div>

        <!-- Waste Calculator -->
        <div class="waste-calculator">
            <div class="calculator-title">Kalkulator Harga Sampah</div>
            <div class="calculator-row">
                <select class="calculator-input" id="wasteType">
                    <option value="" data-price="0">Pilih Jenis Sampah</option>
                    <option value="plastik" data-price="2500">Botol Plastik (Rp 2.500/kg)</option>
                    <option value="kardus" data-price="2000">Kardus (Rp 2.000/kg)</option>
                    <option value="kertas" data-price="1500">Kertas (Rp 1.500/kg)</option>
                    <option value="logam" data-price="5000">Logam (Rp 5.000/kg)</option>
                    <option value="kaca" data-price="500">Kaca (Rp 500/kg)</option>
                </select>
            </div>
            <div class="calculator-row">
                <input type="number" class="calculator-input" id="wasteWeight" placeholder="Berat (kg)" step="0.1">
                <button class="calculator-btn" onclick="calculateWaste()">Hitung</button>
            </div>
            <div class="calculator-result" id="calculatorResult" style="display: none;">Estimasi Harga: <span id="estimatedPrice"></span></div>
        </div>

        <!-- Transactions Section -->
        <div class="transactions-section">
            <div class="section-title">Aktivitas Terbaru</div>
            <div class="transaction-item setor"><div class="transaction-icon setor">📥</div><div class="transaction-info"><div class="transaction-title">Setor Sampah Plastik</div><div class="transaction-detail">3.2 kg × Rp 2.500</div><div class="transaction-date">Hari ini, 09:30</div></div><div class="transaction-amount setor">+Rp 8.000</div></div>
            <div class="transaction-item reward"><div class="transaction-icon reward">🎁</div><div class="transaction-info"><div class="transaction-title">Bonus Konsisten</div><div class="transaction-detail">Setor 7 hari berturut</div><div class="transaction-date">Kemarin, 18:00</div></div><div class="transaction-amount reward">+Rp 5.000</div></div>
            <div class="transaction-item tarik"><div class="transaction-icon tarik">📤</div><div class="transaction-info"><div class="transaction-title">Penarikan Tunai</div><div class="transaction-detail">Transfer ke rekening</div><div class="transaction-date">3 hari lalu, 10:20</div></div><div class="transaction-amount tarik">-Rp 50.000</div></div>
        </div>

        <!-- Floating Action Button -->
        <div class="floating-btn" onclick="showSetor()">📥</div>

        <!-- Bottom Navigation -->
        <div class="bottom-nav">
            <div class="nav-item active" onclick="showBeranda()"><div class="nav-icon">🏠</div><div class="nav-text">Beranda</div></div>
            <div class="nav-item" onclick="showSetor()"><div class="nav-icon">📥</div><div class="nav-text">Setor</div></div>
            <!-- === TOMBOL RIWAYAT BAWAH YANG FUNGSINYA DIUBAH === -->
            <div class="nav-item" onclick="showActivityHistory()"><div class="nav-icon">📊</div><div class="nav-text">Riwayat</div></div>
            <div class="nav-item" onclick="showPanduan()"><div class="nav-icon">📖</div><div class="nav-text">Panduan</div></div>
            <div class="nav-item" onclick="showProfil()"><div class="nav-icon">👤</div><div class="nav-text">Profil</div></div>
        </div>
    </div>
    
    <!-- Struktur Modal (Pop-up) -->
    <div id="modal" class="modal" onclick="closeModal()">
        <div class="modal-content" onclick="event.stopPropagation()">
            <div class="modal-icon" id="modalIcon">♻️</div>
            <h3 class="modal-title" id="modalTitle"></h3>
            <p class="modal-text" id="modalText"></p>
            <button class="modal-btn" onclick="closeModal()">Tutup</button>
        </div>
    </div>

    <script>
        // =========================================================
        // JAVASCRIPT LENGKAP - SEMUA FUNGSI SUDAH DISESUAIKAN
        // =========================================================

        const modal = document.getElementById('modal');
        const modalIcon = document.getElementById('modalIcon');
        const modalTitle = document.getElementById('modalTitle');
        const modalText = document.getElementById('modalText');

        const userData = { balance: 347500 };
        const wastePrices = { "Botol Plastik": 2500, "Kardus": 2000, "Kertas": 1500, "Logam": 5000, "Kaca": 500 };

        function showModal(icon, title, text) {
            modalIcon.textContent = icon;
            modalTitle.textContent = title;
            modalText.textContent = text;
            modal.style.display = 'flex';
        }
        function closeModal() { modal.style.display = 'none'; }

        function setActiveNav(index) {
            document.querySelectorAll('.nav-item').forEach((item, i) => {
                item.classList.toggle('active', i === index);
            });
        }
        
        // --- FUNGSI BARU UNTUK TOMBOL DI KOTAK SALDO ---
        function showTransfer() {
            showModal('💸', 'Transfer & Tarik Saldo', 'Anda dapat mentransfer saldo tabungan sampah Anda ke rekening bank atau menariknya secara tunai di lokasi Bank Sampah ARAS. Hubungi petugas untuk melakukan transaksi.');
        }

        function showRincianSaldo() {
            showModal('🧾', 'Rincian Saldo (Mutasi Keuangan)', 'Fitur ini akan menampilkan daftar semua transaksi yang menambah atau mengurangi saldo Anda, seperti:\n\n• (Setor) +Rp 8.000\n• (Bonus) +Rp 5.000\n• (Tarik) -Rp 50.000\n\nIni adalah catatan keuangan lengkap Anda.');
        }

        function showIsiSaldo() {
            showModal('➕', 'Cara Mengisi Saldo', 'Saldo Anda bertambah setiap kali Anda menyetorkan sampah yang memiliki nilai jual. Semakin banyak sampah yang Anda setor, semakin besar saldo tabungan Anda!');
        }
        
        // --- FUNGSI BARU UNTUK NAVIGASI RIWAYAT DI BAWAH ---
        function showActivityHistory() {
            setActiveNav(2);
            showModal('📊', 'Riwayat Aktivitas', 'Halaman ini akan menampilkan riwayat aktivitas non-keuangan Anda, seperti:\n\n• Setor Sampah Plastik: 3.2 kg\n• Setor Sampah Kardus: 2.5 kg\n• Mengikuti Workshop Daur Ulang\n\nIni adalah catatan partisipasi Anda, bukan catatan keuangan.');
        }

        // --- FUNGSI UNTUK MENU DAN NAVIGASI LAINNYA ---
        function showBeranda() { setActiveNav(0); }
        function showProfil() { setActiveNav(4); showModal('👤', 'Profil Pengguna', 'Di sini Anda dapat melihat data diri, mengubah kata sandi, dan mengatur rekening bank untuk penarikan.'); }
        
        function showSetor() {
            setActiveNav(1);
            showModal('📥', 'Cara Menyetor Sampah', '1. Pilah sampah Anda sesuai jenis.\n2. Pastikan sampah dalam kondisi bersih dan kering.\n3. Bawa sampah ke lokasi Bank Sampah ARAS sesuai jadwal.');
        }

        function showHarga() {
            let priceList = "Daftar harga sampah saat ini (per kg):\n\n";
            for (const [item, price] of Object.entries(wastePrices)) {
                priceList += `• ${item}: Rp ${price.toLocaleString('id-ID')}\n`;
            }
            priceList += "\n*Harga dapat berubah sewaktu-waktu.";
            showModal('💰', 'Daftar Harga Sampah', priceList);
        }

        function showJadwal() {
            showModal('📅', 'Jadwal Operasional', 'Bank Sampah ARAS beroperasi pada:\n\n• Hari: Selasa & Jumat\n• Jam: 08:00 - 16:00 WIB\n\nUntuk permintaan pickup, hubungi pengurus H-1.');
        }

        function showPanduan() {
            setActiveNav(3);
            showModal('📖', 'Panduan Memilah Sampah', '• KERTAS: Koran, HVS, majalah.\n• PLASTIK: Botol, gelas, & kresek.\n• LOGAM: Kaleng minuman/makanan.\n• KACA: Botol sirup, botol kecap.');
        }

        function showLeaderboard() {
            showModal('🏆', 'Leaderboard Nasabah', 'Peringkat setoran terbanyak bulan ini:\n\n1. Bpk. Sutisna (45.2 kg)\n2. Ibu Aisyah (41.8 kg)\n3. Ajis Abdul Jabar (23.0 kg)\n\nTerus tingkatkan setoran Anda!');
        }

        function showReward() {
            showModal('🎁', 'Program Tukar Poin', 'Setiap setoran akan mendapatkan poin yang bisa ditukar dengan hadiah menarik seperti sembako, pulsa, atau voucher belanja. Info lebih lanjut hubungi petugas.');
        }

        // Fungsi Kalkulator Sampah
        function calculateWaste() {
            const wasteTypeSelect = document.getElementById('wasteType');
            const weightInput = document.getElementById('wasteWeight');
            const resultDiv = document.getElementById('calculatorResult');
            const priceSpan = document.getElementById('estimatedPrice');

            const selectedOption = wasteTypeSelect.options[wasteTypeSelect.selectedIndex];
            const price = parseFloat(selectedOption.getAttribute('data-price'));
            const weight = parseFloat(weightInput.value);

            resultDiv.style.display = 'block';

            if (price === 0 || isNaN(weight) || weight <= 0) {
                resultDiv.style.background = 'rgba(231, 76, 60, 0.5)';
                priceSpan.textContent = 'Pilih jenis & isi berat';
                return;
            }

            const total = price * weight;
            resultDiv.style.background = 'rgba(255,255,255,0.1)';
            priceSpan.textContent = `Rp ${total.toLocaleString('id-ID')}`;
        }
    </script>
</body>
</html>
