# 💰 Tip Calculator

**Tugas Pemrograman Perangkat Bergerak**

Aplikasi Android untuk menghitung tip/bakshish secara otomatis berdasarkan jumlah tagihan dan persentase tip yang diinginkan. Dibangun menggunakan **Kotlin** dan **Jetpack Compose**.

---

## ✨ Fitur

- 💵 **Input Jumlah Tagihan** — Masukkan total bill dengan keyboard numerik
- 📊 **Input Persentase Tip** — Tentukan persentase tip sesuai keinginan (default 15%)
- ⬆️ **Round Up Tip** — Opsi pembulatan tip ke atas (ceil)
- 💲 **Hasil Real-time** — Tip amount dihitung dan ditampilkan secara otomatis
- 🌙 **Tema Dinamis** — Mendukung dark mode dan dynamic color (Android 12+)

---

## 🛠️ Teknologi

| Komponen | Versi |
|----------|-------|
| Android Gradle Plugin | 9.1.1 |
| Kotlin | 2.2.10 |
| Compile SDK | 36 |
| Min SDK | 24 (Android 7.0) |
| Target SDK | 36 |
| Jetpack Compose BOM | 2026.02.01 |
| Material Design | 3 (Material3) |

---

## 📂 Struktur Proyek

```
Tip-Calculator/
├── app/
│   ├── build.gradle.kts          # Konfigurasi build aplikasi
│   └── src/
│       └── main/
│           ├── AndroidManifest.xml
│           ├── java/com/example/tipcalculator/
│           │   ├── MainActivity.kt       # Entry point aplikasi
│           │   ├── TipTimeLayout.kt      # UI & logika kalkulasi tip
│           │   └── ui/theme/
│           │       ├── Color.kt          # Definisi warna
│           │       ├── Theme.kt          # Tema aplikasi (light/dark/dynamic)
│           │       └── Type.kt           # Tipografi
│           └── res/
│               └── values/
│                   ├── strings.xml       # String resource
│                   └── themes.xml        # Tema legacy
├── build.gradle.kts              # Konfigurasi build root
├── settings.gradle.kts           # Pengaturan project
├── gradle/
│   └── libs.versions.toml        # Version catalog dependencies
├── gradlew / gradlew.bat         # Gradle wrapper
└── README.md                     # Dokumentasi proyek
```

---

## 🚀 Cara Menjalankan

### Prasyarat
- Android Studio (versi terbaru direkomendasikan)
- JDK 11 atau lebih tinggi
- Android SDK dengan API Level 36

### Langkah-langkah

1. **Clone repository**
   ```bash
   git clone https://github.com/NaufalAhnafussidqi/Tip-Calculator.git
   cd Tip-Calculator
   ```

2. **Buka di Android Studio**
   - Pilih **File → Open** dan arahkan ke folder proyek
   - Tunggu Gradle sync selesai

3. **Jalankan aplikasi**
   - Hubungkan perangkat Android atau buka emulator
   - Klik tombol **Run** (▶️) atau tekan `Shift + F10`

---

## 📝 Penjelasan Kode

### `MainActivity.kt`

Entry point aplikasi yang mengatur tema dan memanggil composable utama:

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            TipCalculatorTheme {
                Surface {
                    TipTimeLayout()
                }
            }
        }
    }
}
```

### `TipTimeLayout.kt`

Composable utama yang menangani UI dan logika perhitungan tip:

| Komponen | Fungsi |
|----------|--------|
| `OutlinedTextField` (Bill Amount) | Input jumlah tagihan dengan keyboard numerik |
| `OutlinedTextField` (Tip Percentage) | Input persentase tip (default 15%) |
| `Switch` (Round Up Tip) | Toggle pembulatan tip ke atas |
| `Text` (Tip Amount) | Menampilkan hasil perhitungan tip dalam format mata uang |

### Logika Perhitungan

```kotlin
val amount = amountInput.toDoubleOrNull() ?: 0.0
val tipPercent = tipInput.toDoubleOrNull() ?: 15.0

var tip = amount * tipPercent / 100

if (roundUp) {
    tip = ceil(tip)  // Pembulatan ke atas
}

val tipAmount = NumberFormat.getCurrencyInstance().format(tip)
```

### `Theme.kt`

Mendukung 3 mode tema:
- **Dynamic Color** — Warna mengikuti tema sistem (Android 12+)
- **Light Theme** — Skema warna terang
- **Dark Theme** — Skema warna gelap

---

## 👤 Author

**Anasufi Ajwa Nazli Nailulhaq**

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan tugas pemrograman perangkat bergerak.
