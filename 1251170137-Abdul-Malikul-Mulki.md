TUGAS ALGORITMA DAN STRUKTUR DATA

## SISTEM TRANSAKSI & VALIDASI TOKO BUKU MODERN

---

# A. IDENTIFIKASI DAN ANALISIS KOMPONEN

## 1. Variabel dan Tipe Data

| No. | Variabel | Tipe Data | Keterangan |
|---|---|---|---|
| 1 | `is_member` | Boolean | Menentukan status keanggotaan pelanggan |
| 2 | `jumlah_buku` | Integer | Menyimpan jumlah buku yang dibeli |
| 3 | `total_awal` | Real/Float | Menyimpan total belanja sebelum diskon |
| 4 | `persentase_diskon` | Real/Float | Menyimpan persentase diskon |
| 5 | `nominal_diskon` | Real/Float | Menyimpan nominal diskon |
| 6 | `total_bayar` | Real/Float | Menyimpan total pembayaran setelah diskon |

## 2. Struktur Kontrol

Algoritma menggunakan tiga struktur kontrol:

### a. (Sequence)

Instruksi dijalankan secara berurutan dari atas ke bawah, seperti proses input data, menghitung diskon, dan menghitung total pembayaran.

### b.  (Selection)

Digunakan untuk menentukan besarnya diskon berdasarkan status pelanggan dan kondisi pembelian menggunakan `IF - THEN - ELSE`.

### c.  (Iteration)

Digunakan untuk melakukan validasi input menggunakan `WHILE`. Jika data tidak valid, pengguna diminta memasukkan data kembali.

---

# B. PENYUSUNAN PSEUDOCODE

Pseudocode disusun berdasarkan tiga bagian utama:

1. Header
2. Deklarasi
3. Algoritma

## 1. Header

```text
PROGRAM SistemTransaksiTokoBuku

2. Deklarasi
DEKLARASI:
    is_member : boolean
    jumlah_buku : integer
    total_awal : real
    persentase_diskon : real
    nominal_diskon : real
    total_bayar : real

3. Algoritma
ALGORITMA:

    INPUT(is_member)
    INPUT(jumlah_buku)
    INPUT(total_awal)

    WHILE (total_awal < 0 OR jumlah_buku < 1) DO
        OUTPUT("Input tidak valid. Silakan masukkan ulang data.")

        INPUT(is_member)
        INPUT(jumlah_buku)
        INPUT(total_awal)
    ENDWHILE

    IF (is_member = TRUE) THEN

        IF (total_awal >= 200000 AND jumlah_buku >= 3) THEN
            persentase_diskon ← 0.15
        ELSE
            persentase_diskon ← 0.10
        ENDIF

    ELSE

        IF (total_awal >= 300000) THEN
            persentase_diskon ← 0.05
        ELSE
            persentase_diskon ← 0
        ENDIF

    ENDIF

    nominal_diskon ← total_awal × persentase_diskon

    total_bayar ← total_awal - nominal_diskon

    OUTPUT("Nominal diskon = ", nominal_diskon)
    OUTPUT("Total bayar = ", total_bayar)

END PROGRAM

C. UJI LOGIKA / TRACE TABLE

# TRACE TABLE
## Sistem Transaksi & Validasi Toko Buku Modern

---

## Kasus A

### Input

```text
is_member = TRUE
jumlah_buku = 4
total_awal = 250000
Trace Table Kasus A
No.
Proses
Nilai/Hasil
1
is_member
TRUE
2
jumlah_buku
4
3
total_awal
Rp250.000
4
total_awal < 0
FALSE
5
jumlah_buku < 1
FALSE
6
Input valid
Ya
7
is_member = TRUE
TRUE
8
total_awal >= 200000
TRUE
9
jumlah_buku >= 3
TRUE
10
persentase_diskon
15%
11
nominal_diskon = 250000 × 15%
Rp37.500
12
total_bayar = 250000 - 37500
Rp212.500

### Hasil Kasus B

- Nominal Diskon = **Rp17.500**
- Total Bayar = **Rp332.500**

### Hasil Kasus C

- Nominal Diskon = **Rp0**
- Total Bayar = **Rp100.000**

## Trace Table Kasus C

### Input Awal

| No. | Proses | Nilai/Hasil |
|---:|---|---|
| 1 | `is_member` | FALSE |
| 2 | `jumlah_buku` | 1 |
| 3 | `total_awal` | -Rp50.000 |
| 4 | `total_awal < 0` | TRUE |
| 5 | `jumlah_buku < 1` | FALSE |
| 6 | Input valid | **Tidak** |
| 7 | Sistem meminta input ulang | Ya |

### Input Setelah Dikoreksi

| No. | Proses | Nilai/Hasil |
|---:|---|---|
| 8 | `is_member` | FALSE |
| 9 | `jumlah_buku` | 1 |
| 10 | `total_awal` | Rp100.000 |
| 11 | `total_awal < 0` | FALSE |
| 12 | `jumlah_buku < 1` | FALSE |
| 13 | Input valid | Ya |
| 14 | `is_member = TRUE` | FALSE |
| 15 | Masuk kondisi Non-Member | Ya |
| 16 | `total_awal >= 300000` | FALSE |
| 17 | `persentase_diskon` | 0% |
| 18 | `nominal_diskon = 100000 × 0%` | Rp0 |
| 19 | `total_bayar = 100000 - 0` | **Rp100.000** |

