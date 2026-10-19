[Uploading pts_fisika_kelas_10_interactive_exam.html…]()
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PTS Fisika Kelas X - Portal Ujian & Dashboard</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Font Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .no-select { user-select: none; -webkit-user-select: none; }
    </style>
</head>
<body class="bg-slate-900 text-slate-100 min-h-screen flex flex-col justify-between">

    <!-- Header -->
    <header class="bg-slate-800 border-b border-slate-700 shadow-lg sticky top-0 z-40">
        <div class="max-w-7xl mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <div class="bg-indigo-600 text-white p-2.5 rounded-xl shadow-md">
                    <i class="fa-solid fa-atom text-2xl animate-spin-slow"></i>
                </div>
                <div>
                    <h1 class="text-xl font-bold text-white tracking-wide">PTS FISIKA KELAS X</h1>
                    <p class="text-xs text-slate-400">SMA Negeri Portal Edukasi • Semester Ganjil</p>
                </div>
            </div>
            <div id="navRight" class="flex items-center space-x-2">
                <span class="inline-flex items-center px-3 py-1 rounded-full text-xs font-medium bg-indigo-500/10 text-indigo-400 border border-indigo-500/20">
                    <span class="w-2 h-2 mr-1.5 rounded-full bg-emerald-400 animate-pulse"></span> Mode Online
                </span>
            </div>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="max-w-7xl mx-auto px-4 py-8 flex-grow w-full">

        <!-- VIEW 1: Role Selection (Halaman Depan) -->
        <div id="viewRoleSelect" class="max-w-md mx-auto bg-slate-800 rounded-2xl border border-slate-700 p-8 shadow-2xl transition-all duration-300">
            <div class="text-center mb-8">
                <div class="w-16 h-16 bg-indigo-600/20 text-indigo-400 rounded-2xl flex items-center justify-center mx-auto mb-4 border border-indigo-500/30">
                    <i class="fa-solid fa-graduation-cap text-3xl"></i>
                </div>
                <h2 class="text-2xl font-bold text-white">Selamat Datang</h2>
                <p class="text-slate-400 text-sm mt-1">Pilih hak akses untuk melanjutkan ke portal ujian</p>
            </div>

            <div class="space-y-4">
                <button onclick="switchView('viewStudentLogin')" class="w-full bg-indigo-600 hover:bg-indigo-500 text-white font-semibold py-4 px-6 rounded-xl shadow-lg transition-all transform hover:-translate-y-0.5 flex items-center justify-between group">
                    <div class="flex items-center space-x-4">
                        <i class="fa-solid fa-user-graduate text-2xl group-hover:scale-110 transition-transform"></i>
                        <div class="text-left">
                            <div class="font-bold">Akses Siswa</div>
                            <div class="text-xs text-indigo-200">Kerjakan Ujian PTS Fisika</div>
                        </div>
                    </div>
                    <i class="fa-solid fa-arrow-right"></i>
                </button>

                <button onclick="openTeacherPinModal()" class="w-full bg-slate-700 hover:bg-slate-600 text-slate-200 font-semibold py-4 px-6 rounded-xl border border-slate-600 transition-all transform hover:-translate-y-0.5 flex items-center justify-between group">
                    <div class="flex items-center space-x-4">
                        <i class="fa-solid fa-user-tie text-2xl group-hover:scale-110 transition-transform text-indigo-400"></i>
                        <div class="text-left">
                            <div class="font-bold">Akses Guru / Pengawas</div>
                            <div class="text-xs text-slate-400">Dashboard & Rekapitulasi Real-Time</div>
                        </div>
                    </div>
                    <i class="fa-solid fa-lock text-sm"></i>
                </button>
            </div>
        </div>

        <!-- VIEW 2: Student Login Form -->
        <div id="viewStudentLogin" class="hidden max-w-md mx-auto bg-slate-800 rounded-2xl border border-slate-700 p-8 shadow-2xl">
            <button onclick="switchView('viewRoleSelect')" class="text-xs text-slate-400 hover:text-white mb-6 flex items-center space-x-1">
                <i class="fa-solid fa-arrow-left"></i> <span>Kembali ke Halaman Depan</span>
            </button>
            
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-white">Identitas Siswa</h2>
                <p class="text-slate-400 text-sm">Lengkapi data Anda sebelum memulai ujian.</p>
            </div>

            <form id="studentLoginForm" onsubmit="handleStudentLogin(event)" class="space-y-5">
                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-slate-300 mb-2">Nama Lengkap</label>
                    <div class="relative">
                        <i class="fa-solid fa-user absolute left-4 top-3.5 text-slate-400"></i>
                        <input type="text" id="studentName" required placeholder="Contoh: Budi Santoso" class="w-full bg-slate-900 border border-slate-700 rounded-xl pl-11 pr-4 py-3 text-sm focus:outline-none focus:border-indigo-500 text-white">
                    </div>
                </div>

                <div>
                    <label class="block text-xs font-semibold uppercase tracking-wider text-slate-300 mb-2">Kelas / Nomor Absen</label>
                    <div class="relative">
                        <i class="fa-solid fa-id-badge absolute left-4 top-3.5 text-slate-400"></i>
                        <input type="text" id="studentClass" required placeholder="Contoh: X IPA 1 / 08" class="w-full bg-slate-900 border border-slate-700 rounded-xl pl-11 pr-4 py-3 text-sm focus:outline-none focus:border-indigo-500 text-white">
                    </div>
                </div>

                <div class="p-4 bg-amber-500/10 border border-amber-500/20 rounded-xl text-xs text-amber-300 space-y-1">
                    <div class="font-semibold flex items-center"><i class="fa-solid fa-triangle-exclamation mr-1.5"></i> Peraturan Ujian:</div>
                    <ul class="list-disc list-inside space-y-0.5 text-amber-200/80">
                        <li>Durasi pengerjaan: 20 Menit.</li>
                        <li>Sistem Anti-Curang aktif (Maks. 3x pindah tab/window).</li>
                        <li>Pindah tab 3x akan mengakibatkan **Auto-Submit & Terkunci**.</li>
                    </ul>
                </div>

                <button type="submit" id="btnStartExam" class="w-full bg-indigo-600 hover:bg-indigo-500 text-white font-semibold py-3.5 px-6 rounded-xl shadow-lg transition-all flex justify-center items-center space-x-2">
                    <span>Mulai Ujian Sekarang</span>
                    <i class="fa-solid fa-play text-xs"></i>
                </button>
            </form>
        </div>

        <!-- VIEW 3: Interactive Exam Interface -->
        <div id="viewExam" class="hidden no-select max-w-4xl mx-auto">
            <!-- Exam Header Bar -->
            <div class="bg-slate-800 rounded-2xl border border-slate-700 p-4 mb-6 shadow-xl flex flex-wrap justify-between items-center gap-4">
                <div>
                    <span id="examStudentInfo" class="text-sm font-semibold text-white">Siswa: -</span>
                    <div class="text-xs text-slate-400">PTS Fisika - Kelas X</div>
                </div>

                <div class="flex items-center space-x-4">
                    <!-- Violation Tracker Badge -->
                    <div class="flex items-center bg-rose-500/10 border border-rose-500/20 px-3 py-1.5 rounded-lg text-rose-400 text-xs font-semibold">
                        <i class="fa-solid fa-shield-halved mr-1.5"></i>
                        <span>Pelanggaran: <span id="violationBadge">0</span>/3</span>
                    </div>

                    <!-- Countdown Timer -->
                    <div class="flex items-center bg-indigo-600/20 border border-indigo-500/30 px-4 py-1.5 rounded-lg text-indigo-300 text-sm font-bold">
                        <i class="fa-solid fa-stopwatch mr-2 animate-pulse"></i>
                        <span id="timerDisplay">20:00</span>
                    </div>
                </div>
            </div>

            <!-- Question Card -->
            <div class="bg-slate-800 rounded-2xl border border-slate-700 p-6 md:p-8 shadow-2xl mb-6">
                <div class="flex justify-between items-center mb-6 border-b border-slate-700 pb-4">
                    <span class="text-xs font-semibold uppercase tracking-wider text-indigo-400 bg-indigo-500/10 px-3 py-1 rounded-full border border-indigo-500/20">
                        Soal <span id="currentQuestionNum">1</span> dari <span id="totalQuestionsNum">5</span>
                    </span>
                    <span class="text-xs text-slate-400" id="questionCategory">Materi: -</span>
                </div>

                <div id="questionText" class="text-lg font-medium text-slate-100 mb-8 leading-relaxed">
                    Loading soal...
                </div>

                <!-- Options -->
                <div id="optionsContainer" class="space-y-3">
                    <!-- Options injected via JS -->
                </div>
            </div>

            <!-- Exam Navigation Footer -->
            <div class="flex justify-between items-center">
                <button id="btnPrev" onclick="navigateQuestion(-1)" class="bg-slate-800 hover:bg-slate-700 text-slate-300 border border-slate-700 font-semibold px-5 py-2.5 rounded-xl transition disabled:opacity-40 disabled:cursor-not-allowed text-sm flex items-center space-x-2">
                    <i class="fa-solid fa-chevron-left"></i> <span>Sebelumnya</span>
                </button>

                <div class="flex space-x-2" id="questionDots">
                    <!-- Dots injected via JS -->
                </div>

                <button id="btnNext" onclick="navigateQuestion(1)" class="bg-indigo-600 hover:bg-indigo-500 text-white font-semibold px-5 py-2.5 rounded-xl transition text-sm flex items-center space-x-2">
                    <span>Berikutnya</span> <i class="fa-solid fa-chevron-right"></i>
                </button>

                <button id="btnSubmitExam" onclick="confirmSubmitExam()" class="hidden bg-emerald-600 hover:bg-emerald-500 text-white font-semibold px-6 py-2.5 rounded-xl shadow-lg transition text-sm flex items-center space-x-2">
                    <i class="fa-solid fa-paper-plane"></i> <span>Kumpulkan Ujian</span>
                </button>
            </div>
        </div>

        <!-- VIEW 4: Student Result Card -->
        <div id="viewResult" class="hidden max-w-md mx-auto bg-slate-800 rounded-2xl border border-slate-700 p-8 shadow-2xl text-center">
            <div id="resultIcon" class="w-20 h-20 bg-emerald-500/20 text-emerald-400 rounded-full flex items-center justify-center mx-auto mb-6 border border-emerald-500/30">
                <i class="fa-solid fa-trophy text-4xl"></i>
            </div>

            <h2 class="text-2xl font-bold text-white mb-1">Ujian Selesai!</h2>
            <p id="resultStatusText" class="text-xs text-slate-400 mb-6">Jawaban Anda berhasil dikirim ke database guru.</p>

            <div class="bg-slate-900 rounded-xl p-6 border border-slate-700/50 mb-6 space-y-4">
                <div class="text-center border-b border-slate-800 pb-4">
                    <div class="text-xs text-slate-400 uppercase tracking-wider mb-1">Nilai Akhir</div>
                    <div id="resultScore" class="text-5xl font-extrabold text-indigo-400">0</div>
                </div>

                <div class="grid grid-cols-2 gap-4 text-left text-xs">
                    <div>
                        <span class="text-slate-400 block">Nama:</span>
                        <span id="resName" class="font-semibold text-slate-200">-</span>
                    </div>
                    <div>
                        <span class="text-slate-400 block">Kelas/Absen:</span>
                        <span id="resClass" class="font-semibold text-slate-200">-</span>
                    </div>
                    <div>
                        <span class="text-slate-400 block">Pelanggaran:</span>
                        <span id="resViolations" class="font-semibold text-slate-200">0x</span>
                    </div>
                    <div>
                        <span class="text-slate-400 block">Status:</span>
                        <span id="resStatus" class="font-semibold text-emerald-400">Selesai</span>
                    </div>
                </div>
            </div>

            <button onclick="location.reload()" class="w-full bg-slate-700 hover:bg-slate-600 text-white font-semibold py-3 px-6 rounded-xl transition text-sm">
                Kembali ke Halaman Depan
            </button>
        </div>

        <!-- VIEW 5: Teacher Dashboard & Live Table -->
        <div id="viewTeacherDashboard" class="hidden max-w-7xl mx-auto space-y-6">
            <!-- Dashboard Header -->
            <div class="bg-slate-800 rounded-2xl border border-slate-700 p-6 shadow-xl flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div>
                    <h2 class="text-2xl font-bold text-white flex items-center gap-2">
                        <i class="fa-solid fa-chart-line text-indigo-400"></i> Dashboard Pengawas & Rekap Nilai
                    </h2>
                    <p class="text-xs text-slate-400 mt-1">Pemantauan real-time hasil ujian dan manajemen status siswa.</p>
                </div>

                <div class="flex flex-wrap items-center gap-3">
                    <button onclick="fetchTeacherData()" class="bg-indigo-600 hover:bg-indigo-500 text-white px-4 py-2.5 rounded-xl text-xs font-semibold shadow transition flex items-center space-x-2">
                        <i class="fa-solid fa-arrows-rotate" id="refreshIcon"></i> <span>Refresh Data</span>
                    </button>
                    <button onclick="exportToCSV()" class="bg-emerald-600 hover:bg-emerald-500 text-white px-4 py-2.5 rounded-xl text-xs font-semibold shadow transition flex items-center space-x-2">
                        <i class="fa-solid fa-file-excel"></i> <span>Ekspor CSV / Excel</span>
                    </button>
                    <button onclick="switchView('viewRoleSelect')" class="bg-slate-700 hover:bg-slate-600 text-slate-300 px-4 py-2.5 rounded-xl text-xs font-semibold transition">
                        Keluar
                    </button>
                </div>
            </div>

            <!-- Stats Summary Cards -->
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4">
                <div class="bg-slate-800 rounded-xl border border-slate-700 p-4 shadow">
                    <div class="text-xs text-slate-400 uppercase">Total Peserta</div>
                    <div id="statTotal" class="text-2xl font-bold text-white mt-1">0</div>
                </div>
                <div class="bg-slate-800 rounded-xl border border-slate-700 p-4 shadow">
                    <div class="text-xs text-slate-400 uppercase">Rata-Rata Nilai</div>
                    <div id="statAvg" class="text-2xl font-bold text-indigo-400 mt-1">0.0</div>
                </div>
                <div class="bg-slate-800 rounded-xl border border-slate-700 p-4 shadow">
                    <div class="text-xs text-slate-400 uppercase">Selesai Normal</div>
                    <div id="statCompleted" class="text-2xl font-bold text-emerald-400 mt-1">0</div>
                </div>
                <div class="bg-slate-800 rounded-xl border border-slate-700 p-4 shadow">
                    <div class="text-xs text-slate-400 uppercase">Terkunci / Melanggar</div>
                    <div id="statLocked" class="text-2xl font-bold text-rose-400 mt-1">0</div>
                </div>
            </div>

            <!-- Controls & Filter -->
            <div class="bg-slate-800 rounded-2xl border border-slate-700 p-4 shadow-xl flex flex-col sm:flex-row justify-between gap-4">
                <div class="relative flex-grow max-w-md">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-3 text-slate-400 text-sm"></i>
                    <input type="text" id="teacherSearchInput" oninput="filterTeacherTable()" placeholder="Cari Nama atau Kelas..." class="w-full bg-slate-900 border border-slate-700 rounded-xl pl-10 pr-4 py-2 text-xs focus:outline-none focus:border-indigo-500 text-white">
                </div>
                <div class="text-xs text-slate-400 flex items-center">
                    Database Source: <span id="dbSourceBadge" class="ml-2 font-mono font-bold text-indigo-400">GAS API</span>
                </div>
            </div>

            <!-- Student Results Table -->
            <div class="bg-slate-800 rounded-2xl border border-slate-700 shadow-xl overflow-hidden">
                <div class="overflow-x-auto">
                    <table class="w-full text-left text-xs text-slate-300">
                        <thead class="bg-slate-900/80 text-slate-400 uppercase tracking-wider border-b border-slate-700">
                            <tr>
                                <th class="p-4">Siswa</th>
                                <th class="p-4">Kelas/Absen</th>
                                <th class="p-4 text-center">Nilai</th>
                                <th class="p-4 text-center">Pelanggaran</th>
                                <th class="p-4">Status</th>
                                <th class="p-4">Waktu Selesai</th>
                                <th class="p-4 text-center">Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="teacherTableBody" class="divide-y divide-slate-700/50">
                            <!-- Injected dynamically via JS -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

    </main>

    <!-- MODAL 1: Teacher PIN Entry -->
    <div id="modalTeacherPin" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-black/70 backdrop-blur-sm p-4">
        <div class="bg-slate-800 rounded-2xl border border-slate-700 p-6 max-w-sm w-full shadow-2xl space-y-4">
            <div class="text-center">
                <div class="w-12 h-12 bg-indigo-600/20 text-indigo-400 rounded-xl flex items-center justify-center mx-auto mb-3 border border-indigo-500/30">
                    <i class="fa-solid fa-key text-xl"></i>
                </div>
                <h3 class="text-lg font-bold text-white">Otentikasi Pengawas</h3>
                <p class="text-xs text-slate-400">Masukkan PIN Guru untuk membuka dashboard.</p>
            </div>

            <div>
                <input type="password" id="teacherPinInput" placeholder="Default PIN: 1234" class="w-full bg-slate-900 border border-slate-700 rounded-xl px-4 py-3 text-center text-lg font-mono tracking-widest focus:outline-none focus:border-indigo-500 text-white">
                <p id="pinErrorMsg" class="text-xs text-rose-400 mt-1.5 text-center hidden">PIN salah, silakan coba lagi!</p>
            </div>

            <div class="flex space-x-3">
                <button onclick="closeTeacherPinModal()" class="w-1/2 bg-slate-700 hover:bg-slate-600 text-slate-300 font-semibold py-2.5 rounded-xl text-xs transition">Batal</button>
                <button onclick="verifyTeacherPin()" class="w-1/2 bg-indigo-600 hover:bg-indigo-500 text-white font-semibold py-2.5 rounded-xl text-xs transition">Masuk</button>
            </div>
        </div>
    </div>

    <!-- MODAL 2: Anti-Cheat Violation Warning -->
    <div id="modalViolation" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-black/80 backdrop-blur-sm p-4">
        <div class="bg-slate-800 rounded-2xl border border-rose-500/50 p-6 max-w-md w-full shadow-2xl text-center space-y-4 animate-bounce-once">
            <div class="w-16 h-16 bg-rose-500/20 text-rose-500 rounded-full flex items-center justify-center mx-auto border border-rose-500/30">
                <i class="fa-solid fa-triangle-exclamation text-3xl"></i>
            </div>
            <h3 class="text-xl font-bold text-white">Peringatan Pelanggaran!</h3>
            <p id="violationModalText" class="text-sm text-slate-300">
                Terdeteksi meninggalkan layar ujian/pindah tab! Pelanggaran dicatat oleh sistem.
            </p>
            <div class="bg-rose-500/10 border border-rose-500/20 p-3 rounded-xl text-rose-400 font-semibold text-sm">
                Catatan Pelanggaran: <span id="modalViolationCount">1</span> / 3
            </div>
            <button onclick="closeViolationModal()" class="w-full bg-rose-600 hover:bg-rose-500 text-white font-semibold py-3 rounded-xl text-xs transition">
                Saya Mengerti & Kembali Pengerjaan
            </button>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-slate-900 border-t border-slate-800 py-4 text-center text-xs text-slate-500">
        &copy; 2026 Portal PTS Fisika Interaktif. Designed for Educational Assessment.
    </footer>

    <script>
        /**
         * =========================================================================================
         *  PANDUAN PENYIAPAN DATABASE ONLINE GRATIS (GOOGLE APPS SCRIPT / GOOGLE SHEETS)
         * =========================================================================================
         * 
         * Langkah-langkah Integrasi Database Online Gratis:
         * 1. Buka Google Sheets baru di https://sheets.google.com
         * 2. Buat header di Baris 1: 
         *    Kolom A: Nama | Kolom B: Kelas | Kolom C: Nilai | Kolom D: Pelanggaran | Kolom E: Status | Kolom F: Waktu
         * 3. Masuk ke menu "Ekstensi" -> "Apps Script".
         * 4. Hapus semua kode default, dan PASTE kode JavaScript Google Apps Script (GAS) di bawah ini:
         * 
         * -----------------------------------------------------------------------------------------
         * KODE GOOGLE APPS SCRIPT (Copy ke editor GAS):
         * -----------------------------------------------------------------------------------------
         * 
            function doGet(e) {
              var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
              var data = sheet.getDataRange().getValues();
              var result = [];
              for (var i = 1; i < data.length; i++) {
                result.push({
                  nama: data[i][0],
                  kelas: data[i][1],
                  nilai: data[i][2],
                  pelanggaran: data[i][3],
                  status: data[i][4],
                  waktu: data[i][5]
                });
              }
              return ContentService.createTextOutput(JSON.stringify(result)).setMimeType(ContentService.MimeType.JSON);
            }

            function doPost(e) {
              var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
              var contents = JSON.parse(e.postData.contents);
              var action = contents.action;
              
              if (action === 'save_result') {
                var data = sheet.getDataRange().getValues();
                var foundRow = -1;
                for (var i = 1; i < data.length; i++) {
                  if (data[i][0] == contents.nama && data[i][1] == contents.kelas) {
                    foundRow = i + 1;
                    break;
                  }
                }
                if (foundRow !== -1) {
                  sheet.getRange(foundRow, 3, 1, 4).setValues([[contents.nilai, contents.pelanggaran, contents.status, contents.waktu]]);
                } else {
                  sheet.appendRow([contents.nama, contents.kelas, contents.nilai, contents.pelanggaran, contents.status, contents.waktu]);
                }
                return ContentService.createTextOutput(JSON.stringify({status: 'success'})).setMimeType(ContentService.MimeType.JSON);
              }
              
              if (action === 'reset_access') {
                var data = sheet.getDataRange().getValues();
                for (var i = 1; i < data.length; i++) {
                  if (data[i][0] == contents.nama && data[i][1] == contents.kelas) {
                    sheet.getRange(i + 1, 5).setValue('Reset');
                    break;
                  }
                }
                return ContentService.createTextOutput(JSON.stringify({status: 'reset_success'})).setMimeType(ContentService.MimeType.JSON);
              }
            }
         * -----------------------------------------------------------------------------------------
         * 5. Klik "Terapkan" (Deploy) -> "Penerapan Baru" (New Deployment).
         * 6. Pilih Jenis: "Aplikasi Web" (Web App).
         * 7. Ubah "Who has access" / "Siapa yang memiliki akses" menjadi "Anyone" / "Siapa Saja".
         * 8. Klik "Deploy", izinkan akses akun, lalu salin "Web App URL" yang diberikan.
         * 9. Tempelkan Web App URL tersebut ke variabel API_URL di bawah ini:
         */

        // KONFIGURASI API DATABASE ONLINE (Google Apps Script Web App URL)
        // Masukkan Web App URL hasil Deploy Google Apps Script Anda di sini.
        // Jika dikosongkan (""), aplikasi otomatis beralih ke fallback LocalStorage internal.
        const API_URL = "https://script.google.com/macros/s/AKfycbxHegYPrZmVHM-EvdnsCvUl4TCzZvcg0W4C5ivOs0sUTW8jVkGC57LkYL67apNRcQSGOg/exec";

        // PIN Default untuk Pengawas/Guru
        const TEACHER_PIN = "1234";

        // Master Soal Fisika Kelas 10 (Minimal 5 Soal)
        const EXAM_QUESTIONS = [
            {
                id: 1,
                category: "Besaran & Satuan",
                question: "Sebuah benda memiliki massa jenis sebesar 2,5 g/cm³. Jika dinyatakan dalam Satuan Internasional (SI), berapa nilai massa jenis benda tersebut?",
                options: [
                    "0,0025 kg/m³",
                    "25 kg/m³",
                    "250 kg/m³",
                    "2.500 kg/m³",
                    "25.000 kg/m³"
                ],
                answer: 3 // Option D (2.500 kg/m³)
            },
            {
                id: 2,
                category: "Vektor",
                question: "Dua buah gaya F₁ = 6 N dan F₂ = 8 N saling tegak lurus (membentuk sudut 90°). Besarnya resultan kedua gaya tersebut adalah...",
                options: [
                    "2 N",
                    "10 N",
                    "14 N",
                    "48 N",
                    "100 N"
                ],
                answer: 1 // Option B (10 N)
            },
            {
                id: 3,
                category: "Kinematika (GLB)",
                question: "Sebuah mobil bergerak lurus beraturan (GLB) dengan kecepatan konstan 72 km/jam. Jarak yang ditempuh mobil tersebut dalam waktu 10 detik adalah...",
                options: [
                    "72 meter",
                    "150 meter",
                    "200 meter",
                    "360 meter",
                    "720 meter"
                ],
                answer: 2 // Option C (200 m) -> 72 km/h = 20 m/s * 10s = 200m
            },
            {
                id: 4,
                category: "Kinematika (GLBB)",
                question: "Sebuah benda bergerak dari keadaan diam dengan percepatan tetap 2 m/s². Kecepatan benda tersebut setelah bergerak selama 5 detik adalah...",
                options: [
                    "5 m/s",
                    "10 m/s",
                    "20 m/s",
                    "25 m/s",
                    "50 m/s"
                ],
                answer: 1 // Option B (10 m/s) -> v = a*t = 2*5 = 10
            },
            {
                id: 5,
                category: "Hukum Newton",
                question: "Sebuah balok bermassa 5 kg ditarik dengan gaya horizontal F = 20 N di atas lantai licin. Percepatan yang dialami balok tersebut adalah...",
                options: [
                    "2 m/s²",
                    "4 m/s²",
                    "5 m/s²",
                    "100 m/s²",
                    "0,25 m/s²"
                ],
                answer: 1 // Option B (4 m/s²) -> a = F/m = 20/5 = 4
            }
        ];

        // Global State Variables
        let currentStudent = { name: "", class: "" };
        let studentAnswers = {};
        let currentQuestionIndex = 0;
        let violationCount = 0;
        let examTimerInterval = null;
        let remainingSeconds = 20 * 60; // 20 Menit
        let isExamActive = false;
        let allTeacherData = [];

        // Switch Views (Single-Page Navigation)
        function switchView(viewId) {
            const views = ['viewRoleSelect', 'viewStudentLogin', 'viewExam', 'viewResult', 'viewTeacherDashboard'];
            views.forEach(id => {
                const el = document.getElementById(id);
                if (el) el.classList.add('hidden');
            });

            const target = document.getElementById(viewId);
            if (target) target.classList.remove('hidden');

            // Update Database Source Indicator
            const badge = document.getElementById('dbSourceBadge');
            if (badge) {
                badge.textContent = API_URL ? "GAS Online API" : "LocalStorage (Fallback)";
            }
        }

        // --- STUDENT MODULE & LOGIN VALIDATION ---
        async function handleStudentLogin(e) {
            e.preventDefault();
            const nameInput = document.getElementById('studentName').value.trim();
            const classInput = document.getElementById('studentClass').value.trim();

            if (!nameInput || !classInput) return;

            const btn = document.getElementById('btnStartExam');
            btn.disabled = true;
            btn.innerHTML = `<i class="fa-solid fa-spinner animate-spin"></i> <span>Memeriksa Status...</span>`;

            currentStudent = { name: nameInput, class: classInput };

            // Check if student already submitted or locked
            const statusCheck = await checkStudentStatusOnline(currentStudent.name, currentStudent.class);

            btn.disabled = false;
            btn.innerHTML = `<span>Mulai Ujian Sekarang</span> <i class="fa-solid fa-play text-xs"></i>`;

            if (statusCheck.isBlocked) {
                alert(`Akses Ditolak!\nStatus Anda: "${statusCheck.status}". Anda sudah mengerjakan atau akun Anda terkunci oleh pengawas.`);
                return;
            }

            // Start Exam Init
            startExamSession();
        }

        // Validate online status
        async function checkStudentStatusOnline(name, studentClass) {
            let data = [];

            if (API_URL) {
                try {
                    const res = await fetch(API_URL);
                    data = await res.json();
                } catch (err) {
                    console.warn("Gagal terhubung ke API online. Memakai LocalStorage fallback.", err);
                    data = getLocalStorageData();
                }
            } else {
                data = getLocalStorageData();
            }

            const existing = data.find(item => item.nama.toLowerCase() === name.toLowerCase() && item.kelas.toLowerCase() === studentClass.toLowerCase());
            if (existing && (existing.status === 'Selesai' || existing.status.includes('Terkunci'))) {
                return { isBlocked: true, status: existing.status };
            }
            return { isBlocked: false };
        }

        function startExamSession() {
            studentAnswers = {};
            currentQuestionIndex = 0;
            violationCount = 0;
            remainingSeconds = 20 * 60;
            isExamActive = true;

            document.getElementById('examStudentInfo').textContent = `Siswa: ${currentStudent.name} (${currentStudent.class})`;
            document.getElementById('violationBadge').textContent = '0';

            switchView('viewExam');
            renderQuestion();
            renderDots();
            startTimer();

            // Enable Anti-Cheat Listeners
            window.addEventListener('blur', handleAntiCheatViolation);
            document.addEventListener('visibilitychange', handleVisibilityChange);
        }

        function renderQuestion() {
            const q = EXAM_QUESTIONS[currentQuestionIndex];
            document.getElementById('currentQuestionNum').textContent = currentQuestionIndex + 1;
            document.getElementById('totalQuestionsNum').textContent = EXAM_QUESTIONS.length;
            document.getElementById('questionCategory').textContent = `Materi: ${q.category}`;
            document.getElementById('questionText').textContent = q.question;

            const container = document.getElementById('optionsContainer');
            container.innerHTML = '';

            const optionLetters = ['A', 'B', 'C', 'D', 'E'];
            q.options.forEach((optText, idx) => {
                const isSelected = studentAnswers[q.id] === idx;
                const optionBtn = document.createElement('div');
                optionBtn.className = `p-4 rounded-xl border cursor-pointer transition flex items-center space-x-3 ${
                    isSelected 
                        ? 'bg-indigo-600/20 border-indigo-500 text-white font-medium' 
                        : 'bg-slate-900/60 border-slate-700/80 hover:bg-slate-700/50 text-slate-300'
                }`;
                optionBtn.onclick = () => selectOption(q.id, idx);
                optionBtn.innerHTML = `
                    <div class="w-7 h-7 rounded-lg flex items-center justify-center font-bold text-xs ${
                        isSelected ? 'bg-indigo-600 text-white' : 'bg-slate-800 text-slate-400 border border-slate-700'
                    }">${optionLetters[idx]}</div>
                    <div class="text-sm flex-grow">${optText}</div>
                `;
                container.appendChild(optionBtn);
            });

            // Navigation button state
            document.getElementById('btnPrev').disabled = currentQuestionIndex === 0;
            
            if (currentQuestionIndex === EXAM_QUESTIONS.length - 1) {
                document.getElementById('btnNext').classList.add('hidden');
                document.getElementById('btnSubmitExam').classList.remove('hidden');
            } else {
                document.getElementById('btnNext').classList.remove('hidden');
                document.getElementById('btnSubmitExam').classList.add('hidden');
            }

            updateDots();
        }

        function selectOption(questionId, optionIndex) {
            studentAnswers[questionId] = optionIndex;
            renderQuestion();
        }

        function navigateQuestion(direction) {
            currentQuestionIndex += direction;
            if (currentQuestionIndex < 0) currentQuestionIndex = 0;
            if (currentQuestionIndex >= EXAM_QUESTIONS.length) currentQuestionIndex = EXAM_QUESTIONS.length - 1;
            renderQuestion();
        }

        function renderDots() {
            const container = document.getElementById('questionDots');
            container.innerHTML = '';
            EXAM_QUESTIONS.forEach((_, idx) => {
                const dot = document.createElement('button');
                dot.id = `dot-${idx}`;
                dot.onclick = () => { currentQuestionIndex = idx; renderQuestion(); };
                dot.className = `w-8 h-8 rounded-lg text-xs font-semibold flex items-center justify-center transition border border-slate-700 bg-slate-800 text-slate-400`;
                dot.textContent = idx + 1;
                container.appendChild(dot);
            });
            updateDots();
        }

        function updateDots() {
            EXAM_QUESTIONS.forEach((q, idx) => {
                const dot = document.getElementById(`dot-${idx}`);
                if (!dot) return;

                const isAnswered = studentAnswers[q.id] !== undefined;
                const isCurrent = currentQuestionIndex === idx;

                if (isCurrent) {
                    dot.className = "w-8 h-8 rounded-lg text-xs font-bold flex items-center justify-center transition border-2 border-indigo-400 bg-indigo-600 text-white shadow-lg";
                } else if (isAnswered) {
                    dot.className = "w-8 h-8 rounded-lg text-xs font-semibold flex items-center justify-center transition bg-emerald-600/30 border border-emerald-500/40 text-emerald-300";
                } else {
                    dot.className = "w-8 h-8 rounded-lg text-xs font-semibold flex items-center justify-center transition border border-slate-700 bg-slate-800 text-slate-400 hover:bg-slate-700";
                }
            });
        }

        // Timer Handling
        function startTimer() {
            clearInterval(examTimerInterval);
            examTimerInterval = setInterval(() => {
                remainingSeconds--;
                const mins = Math.floor(remainingSeconds / 60);
                const secs = remainingSeconds % 60;
                document.getElementById('timerDisplay').textContent = 
                    `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;

                if (remainingSeconds <= 0) {
                    clearInterval(examTimerInterval);
                    alert("Waktu ujian telah habis! Sistem akan mengumpulkan jawaban Anda secara otomatis.");
                    submitExamProcess("Waktu Habis");
                }
            }, 1000);
        }

        // Anti-Cheat Handlers
        function handleVisibilityChange() {
            if (document.hidden && isExamActive) {
                triggerCheatViolation();
            }
        }

        function handleAntiCheatViolation() {
            if (isExamActive) {
                triggerCheatViolation();
            }
        }

        function triggerCheatViolation() {
            violationCount++;
            document.getElementById('violationBadge').textContent = violationCount;

            if (violationCount >= 3) {
                isExamActive = false;
                window.removeEventListener('blur', handleAntiCheatViolation);
                document.removeEventListener('visibilitychange', handleVisibilityChange);
                
                alert("Sistem Terkunci!\nAnda telah meninggalkan layar ujian sebanyak 3 kali. Ujian dihentikan secara otomatis.");
                submitExamProcess("Terkunci (Melanggar)");
            } else {
                document.getElementById('modalViolationCount').textContent = violationCount;
                document.getElementById('modalViolation').classList.remove('hidden');
            }
        }

        function closeViolationModal() {
            document.getElementById('modalViolation').classList.add('hidden');
        }

        // Confirmation Submit
        function confirmSubmitExam() {
            const answeredCount = Object.keys(studentAnswers).length;
            const total = EXAM_QUESTIONS.length;
            
            let msg = `Yakin ingin mengumpulkan ujian sekarang?\n`;
            if (answeredCount < total) {
                msg += `Peringatan: Anda baru menjawab ${answeredCount} dari ${total} soal!`;
            }

            if (confirm(msg)) {
                submitExamProcess("Selesai");
            }
        }

        // Auto Grade & Submit to Online Database
        async function submitExamProcess(status) {
            isExamActive = false;
            clearInterval(examTimerInterval);
            window.removeEventListener('blur', handleAntiCheatViolation);
            document.removeEventListener('visibilitychange', handleVisibilityChange);

            // Calculate Score
            let correctCount = 0;
            EXAM_QUESTIONS.forEach(q => {
                if (studentAnswers[q.id] === q.answer) {
                    correctCount++;
                }
            });

            const finalScore = Math.round((correctCount / EXAM_QUESTIONS.length) * 100);
            const now = new Date();
            const timeFormatted = `${now.getHours().toString().padStart(2,'0')}:${now.getMinutes().toString().padStart(2,'0')} - ${now.getDate()}/${now.getMonth()+1}/${now.getFullYear()}`;

            const payload = {
                action: 'save_result',
                nama: currentStudent.name,
                kelas: currentStudent.class,
                nilai: finalScore,
                pelanggaran: violationCount,
                status: status,
                waktu: timeFormatted
            };

            // Send Data to GAS / LocalStorage
            if (API_URL) {
                try {
                    await fetch(API_URL, {
                        method: 'POST',
                        mode: 'no-cors',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });
                } catch (e) {
                    console.error("Gagal mengirim ke GAS, menyimpan ke LocalStorage fallback.", e);
                    saveToLocalStorage(payload);
                }
            } else {
                saveToLocalStorage(payload);
            }

            // Display Result Card UI
            document.getElementById('resultScore').textContent = finalScore;
            document.getElementById('resName').textContent = currentStudent.name;
            document.getElementById('resClass').textContent = currentStudent.class;
            document.getElementById('resViolations').textContent = `${violationCount}x`;
            
            const resStatusEl = document.getElementById('resStatus');
            resStatusEl.textContent = status;
            if (status.includes('Terkunci')) {
                resStatusEl.className = "font-semibold text-rose-400";
                document.getElementById('resultIcon').className = "w-20 h-20 bg-rose-500/20 text-rose-500 rounded-full flex items-center justify-center mx-auto mb-6 border border-rose-500/30";
            } else {
                resStatusEl.className = "font-semibold text-emerald-400";
            }

            switchView('viewResult');
        }

        // --- TEACHER ACCESS MODULE ---
        function openTeacherPinModal() {
            document.getElementById('teacherPinInput').value = '';
            document.getElementById('pinErrorMsg').classList.add('hidden');
            document.getElementById('modalTeacherPin').classList.remove('hidden');
        }

        function closeTeacherPinModal() {
            document.getElementById('modalTeacherPin').classList.add('hidden');
        }

        function verifyTeacherPin() {
            const input = document.getElementById('teacherPinInput').value;
            if (input === TEACHER_PIN) {
                closeTeacherPinModal();
                switchView('viewTeacherDashboard');
                fetchTeacherData();
            } else {
                document.getElementById('pinErrorMsg').classList.remove('hidden');
            }
        }

        async function fetchTeacherData() {
            const icon = document.getElementById('refreshIcon');
            if (icon) icon.classList.add('animate-spin');

            if (API_URL) {
                try {
                    const res = await fetch(API_URL);
                    allTeacherData = await res.json();
                } catch (e) {
                    console.warn("Gagal fetching GAS API, memakai LocalStorage", e);
                    allTeacherData = getLocalStorageData();
                }
            } else {
                allTeacherData = getLocalStorageData();
            }

            if (icon) icon.classList.remove('animate-spin');
            renderTeacherTable(allTeacherData);
        }

        function renderTeacherTable(data) {
            const tbody = document.getElementById('teacherTableBody');
            tbody.innerHTML = '';

            let total = data.length;
            let totalScore = 0;
            let completed = 0;
            let locked = 0;

            if (total === 0) {
                tbody.innerHTML = `<tr><td colspan="7" class="text-center py-8 text-slate-500">Belum ada data pengerjaan siswa.</td></tr>`;
            } else {
                data.forEach((item) => {
                    totalScore += Number(item.nilai) || 0;
                    if (item.status === 'Selesai') completed++;
                    if (item.status.includes('Terkunci')) locked++;

                    const tr = document.createElement('tr');
                    tr.className = "hover:bg-slate-700/30 transition";

                    let statusBadge = `<span class="bg-emerald-500/10 text-emerald-400 border border-emerald-500/20 px-2.5 py-1 rounded-full font-medium text-xs">${item.status}</span>`;
                    if (item.status.includes('Terkunci')) {
                        statusBadge = `<span class="bg-rose-500/10 text-rose-400 border border-rose-500/20 px-2.5 py-1 rounded-full font-medium text-xs">${item.status}</span>`;
                    } else if (item.status === 'Reset') {
                        statusBadge = `<span class="bg-amber-500/10 text-amber-400 border border-amber-500/20 px-2.5 py-1 rounded-full font-medium text-xs">Akses Direset</span>`;
                    }

                    tr.innerHTML = `
                        <td class="p-4 font-semibold text-white">${escapeHtml(item.nama)}</td>
                        <td class="p-4 text-slate-300">${escapeHtml(item.kelas)}</td>
                        <td class="p-4 text-center font-mono font-bold text-indigo-400">${item.nilai}</td>
                        <td class="p-4 text-center font-semibold ${item.pelanggaran > 0 ? 'text-rose-400' : 'text-slate-400'}">${item.pelanggaran}x</td>
                        <td class="p-4">${statusBadge}</td>
                        <td class="p-4 text-slate-400 text-xs">${item.waktu || '-'}</td>
                        <td class="p-4 text-center">
                            <button onclick="resetStudentAccess('${escapeHtml(item.nama)}', '${escapeHtml(item.kelas)}')" class="bg-amber-600/20 hover:bg-amber-600/40 text-amber-300 border border-amber-500/30 px-3 py-1.5 rounded-lg transition text-xs font-semibold flex items-center justify-center mx-auto space-x-1">
                                <i class="fa-solid fa-rotate-left"></i> <span>Reset Ujian</span>
                            </button>
                        </td>
                    `;
                    tbody.appendChild(tr);
                });
            }

            // Update Summary Stats
            document.getElementById('statTotal').textContent = total;
            document.getElementById('statAvg').textContent = total > 0 ? (totalScore / total).toFixed(1) : "0.0";
            document.getElementById('statCompleted').textContent = completed;
            document.getElementById('statLocked').textContent = locked;
        }

        function filterTeacherTable() {
            const query = document.getElementById('teacherSearchInput').value.toLowerCase();
            const filtered = allTeacherData.filter(item => 
                item.nama.toLowerCase().includes(query) || item.kelas.toLowerCase().includes(query)
            );
            renderTeacherTable(filtered);
        }

        async function resetStudentAccess(nama, kelas) {
            if (!confirm(`Reset akses ujian untuk siswa "${nama}" (${kelas})?\nSiswa ini akan diperbolehkan untuk login dan mengulang pengerjaan.`)) return;

            const payload = {
                action: 'reset_access',
                nama: nama,
                kelas: kelas
            };

            if (API_URL) {
                try {
                    await fetch(API_URL, {
                        method: 'POST',
                        mode: 'no-cors',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });
                    alert("Permintaan Reset berhasil dikirim ke database!");
                } catch (e) {
                    console.error("Gagal reset via GAS, mereset LocalStorage", e);
                    resetLocalStorageData(nama, kelas);
                }
            } else {
                resetLocalStorageData(nama, kelas);
            }

            setTimeout(fetchTeacherData, 800);
        }

        // Export Table to CSV
        function exportToCSV() {
            if (!allTeacherData || allTeacherData.length === 0) {
                alert("Tidak ada data rekap untuk diekspor!");
                return;
            }

            let csvContent = "data:text/csv;charset=utf-8,";
            csvContent += "Nama,Kelas/Absen,Nilai,Pelanggaran,Status,Waktu Selesai\n";

            allTeacherData.forEach(row => {
                csvContent += `"${row.nama}","${row.kelas}","${row.nilai}","${row.pelanggaran}","${row.status}","${row.waktu}"\n`;
            });

            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", `Rekap_PTS_Fisika_Kelas_X_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }

        // LocalStorage Fallback Helper Functions
        function getLocalStorageData() {
            const data = localStorage.getItem('pts_physics_results');
            return data ? JSON.parse(data) : [];
        }

        function saveToLocalStorage(payload) {
            let data = getLocalStorageData();
            const index = data.findIndex(i => i.nama.toLowerCase() === payload.nama.toLowerCase() && i.kelas.toLowerCase() === payload.kelas.toLowerCase());
            
            if (index !== -1) {
                data[index] = payload;
            } else {
                data.push(payload);
            }
            localStorage.setItem('pts_physics_results', JSON.stringify(data));
        }

        function resetLocalStorageData(nama, kelas) {
            let data = getLocalStorageData();
            const index = data.findIndex(i => i.nama.toLowerCase() === nama.toLowerCase() && i.kelas.toLowerCase() === kelas.toLowerCase());
            if (index !== -1) {
                data[index].status = 'Reset';
                localStorage.setItem('pts_physics_results', JSON.stringify(data));
            }
        }

        // XSS Prevention Utility
        function escapeHtml(str) {
            if (!str) return '';
            return str.replace(/[&<>"']/g, function(m) {
                return {
                    '&': '&amp;',
                    '<': '&lt;',
                    '>': '&gt;',
                    '"': '&quot;',
                    "'": '&#039;'
                }[m];
            });
        }
    </script>
</body>
</html>
