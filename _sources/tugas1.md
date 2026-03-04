# Sistem Persamaan Linear

## A. Definisi Sistem Persamaan Linear

Sistem persamaan linear adalah sekumpulan persamaan linear yang terdiri dari beberapa variabel, bisa dua atau tiga variabel. Tujuan sistem persamaan linear ini adalah menentukan nilai variable yang dapat menyelesaikan persamaan(solusi).

**Contoh:**

$
\begin{aligned}
x + y &= 5\\
2x - y &= 1\\
3x + 2y - z &= 1
\end{aligned}
$

**Bentuk Umum:**

$$
\begin{aligned}
a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n &= b_1 \\
a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n &= b_2 \\
\vdots \qquad\qquad\qquad\quad\;\; &\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \cdots + a_{mn}x_n &= b_m
\end{aligned}
$$

Keterangan:

$a_{ij}$ : Koefisien variabel  

$x_{i}$ : Variabel  

$b_{i}$ : Konstanta

Sumber: (https://id.wikipedia.org/wiki/Sistem_persamaan_linear)


Ada kemungkinan solusi yang dapat terjadi pada sistem persamaan linear

## B. Jenis Solusi

1. **Solusi Tunggal:** Hanya terdapat satu nilai variabel yang memenuhi semua persamaan
2. **Solusi Tak Hingga:** Terdapat banyak solusi yang memenuhi semua persamaan
3. **Tidak Ada Solusi:** Tidak ada solusi sama sekali memenuhi suatu persamaan

Untuk solusi SPL dengan 2 variabel pada grafik geometri akan membentuk garis. Bisa berupa garis berimpit, berpotongan, atau sejajar. Sedangkan untuk 3 variabel akan membentuk bidang.

Sumber: (https://informatika.stei.itb.ac.id/~rinaldi.munir/AljabarGeometri/2020-2021/Algeo-04-Tiga-Kemungkinan-Solusi-SPL.pdf)


## C. Metode Penyelesaian Sistem Persamaan Linear

1. **Metode Substitusi:** menyatakan satu variabel dalam bentuk variabel lain, lalu menggantinya ke persamaan berbeda.(sistem sederhana)

2. **Metode Eliminasi:** menghapus salah satu variabel dengan menjumlahkan atau mengurangkan persamaan sehingga jumlah variabel berkurang.

3. **Metode Matriks (Eliminasi Gauss/Gaus-Jordan):** Sistem diubah menjadi bentuk matriks, kemudian dilakukan operasi baris elementer untuk menemukan solusi.

4. **Aturan Cramer:** Menggunakan nilai determinan matriks untuk menemukan solusi

5. **Metode Numerik (Iterasi):**
Misalnya, metode Jacobi atau Gauss-Seidel.

Sumber: _PPT Pertemuan 2 KAL_

Kali ini kita akan bahas penyelesaian SPL menggunakan metode **Metode Matriks (Eliminasi Gauss/Gaus-Jordan)** yaitu menggunakan **operasi baris elementer**

Dalam OBE setiap perubahan matriks selalu berasal dari salah satu dari 3 operasi berikut:

- Menukar baris
- Mengali baris
- Menambah kelipatan baris


## D. Penyelesaian Sistem Persamaan Linear dengan Oprasi Baris Elementer beserta Kode Python

### 1. Solusi Tunggal

$$
\begin{cases}
x + y &= 5 \\
2x - y &= 1
\end{cases}
$$

**Matriks**
$
\left[
\begin{array}{cc|c}
1 & 1 & 5 \\
2 & -1 & 1
\end{array}
\right]
$

**Langkah OBE:**

Hilangkan elemen di bawah pivot pertama.

Untuk menghilangkan elemen di bawah pivot pertama, dilakukan operasi baris  
$R_2 \leftarrow R_2 - 2R_1$, lakukan -2 dikali baris 1 kemudian ditambah dengan baris 2, sehingga elemen di kolom pertama baris kedua menjadi nol.

$$
\left[
\begin{array}{cc|c}
1 & 1 & 5 \\
0 & -3 & -9
\end{array}
\right]
$$

Buat pivot kedua menjadi 1:

Untuk membuat pivot kedua menjadi 1, dilakukan operasi baris  
$R_2 \leftarrow -\frac{1}{3}R_2$, Bagi dengan -3 pada baris 2, sehingga nilai pivot yang semula $-3$ berubah menjadi $1$.

$$
\left[
\begin{array}{cc|c}
1 & 1 & 5 \\
0 & 1 & 3
\end{array}
\right]
$$

**Bentuk Persamaan:**
$
\begin{aligned}
x + y &= 5\\
y &= 3
\end{aligned}
$

kode python:

```python
import sympy as sp
sp.init_printing()

# Matriks awal
A = sp.Matrix([
    [1, 1, 5],
    [2, -1, 1]
])

print("Matriks Awal:")
sp.pprint(A)

# OBE 1
A1 = A.copy()
A1[1,:] = A1.row(1) - 2*A1.row(0)

print("\nHasil OBE 1 (R2 = R2 - 2R1):")
sp.pprint(A1)

# OBE 2
A2 = A1.copy()
A2[1,:] = (-sp.Rational(1,3))*A2.row(1)

print("\nHasil OBE 2 (R2 = -1/3 R2):")
sp.pprint(A2)
```

**Menentukan Solusi**

Baris kedua:
$
y = 3
$

Substitusi ke persamaan pertama:
$
x + 3 = 5 \Rightarrow x = 2
$

Solusi sistem:
$
(x,y) = (2,3)
$

### 2. Solusi Tak Hingga

$$
\begin{cases}
x + y + z &= 4 \\
2x + 3y + z &= 9 \\
3x + 4y + 2z &= 13
\end{cases}
$$

**Matriks**
$
\left[
\begin{array}{ccc|c}
1 & 1 & 1 & 4 \\
2 & 3 & 1 & 9 \\
3 & 4 & 2 & 13
\end{array}
\right]
$

**Langkah OBE:**

Hilangkan elemen di bawah pivot pertama dengan operasi baris:

$R_2 \leftarrow R_2 - 2R_1$  
$R_3 \leftarrow R_3 - 3R_1$

Lakukan -2 dikali baris 1 kemudian ditambah dengan baris 2, sehingga elemen pada kolom pertama di bawah pivot menjadi nol. Pada baris 3 juga lakukan -3 dikali baris 1 kemudian ditambah dengan baris 3.

$$
\left[
\begin{array}{ccc|c}
1 & 1 & 1 & 4 \\
0 & 1 & -1 & 1 \\
0 & 1 & -1 & 1
\end{array}
\right]
$$

Hilangkan elemen pada baris ketiga kolom kedua dengan operasi:

$R_3 \leftarrow R_3 - R_2$

yaitu baris ketiga dikurangi baris kedua sehingga seluruh elemen pada baris ketiga menjadi nol.

$$
\left[
\begin{array}{ccc|c}
1 & 1 & 1 & 4 \\
0 & 1 & -1 & 1 \\
0 & 0 & 0 & 0
\end{array}
\right]
$$

**Bentuk Persamaan:**
$
\begin{aligned}
x + y + z &= 4 \\
y - z &= 1
\end{aligned}
$

Karena ada satu baris nol → variabel bebas ada 1 = **tak hingga solusi**

kode python:

```python
import sympy as sp

# Matriks augmented
A = sp.Matrix([
    [1,1,1,4],
    [2,3,1,9],
    [3,4,2,13]
])

print("Matriks awal:")
sp.pprint(A)

# OBE 1
A[1,:] = A.row(1) - 2*A.row(0)
A[2,:] = A.row(2) - 3*A.row(0)

print("\nSetelah OBE pertama:")
sp.pprint(A)

# OBE 2
A[2,:] = A.row(2) - A.row(1)

print("\nSetelah OBE kedua:")
sp.pprint(A)
```

**Menentukan Solusi**

Misalkan:

$
z = t
$

Dari persamaan kedua:

$
y = 1 + t
$

Substitusi ke persamaan pertama:

$
x + (1+t) + t = 4
$
$
x = 3 - 2t
$

**Himpunan Solusi**
$
(x,y,z) = (3 - 2t,\; 1 + t,\; t), \quad t \in \mathbb{R}
$

### 3. Tidak Ada Solusi

$$
\begin{cases}
x + y = 2 \\
x + y = 5
\end{cases}
$$

**Matriks Awal**

$$
\left[
\begin{array}{cc|c}
1 & 1 & 2 \\
1 & 1 & 5
\end{array}
\right]
$$

**Langkah OBE**

Kurangkan baris kedua dengan baris pertama:

$$
R_2 \leftarrow R_2 - R_1
$$

$$
\left[
\begin{array}{cc|c}
1 & 1 & 2 \\
0 & 0 & 3
\end{array}
\right]
$$

Hasil akhir menyatakan:

$$
0x + 0y = 3 \Rightarrow 0 = 3
$$

kode python:

```python
import sympy as sp
sp.init_printing()

# Matriks awal
A = sp.Matrix([
    [1,1,2],
    [1,1,5]
])

print("Matriks Awal:")
sp.pprint(A)

# OBE 1
A1 = A.copy()
A1[1,:] = A1.row(1) - A1.row(0)

print("\nSetelah OBE (R2 = R2 - R1):")
sp.pprint(A1)
print()
print("0x + 0y = 3  →  kontradiksi")
```

Karena kontradiksi, maka sistem **tidak memiliki solusi**.

$
S = \varnothing
$

## E. Visualisasi Geometri (Geogebra)

### 1. Solusi Tunggal (Garis Berpotongan)

<iframe src="https://www.geogebra.org/calculator/amytm5zw?embed" width="800" height="600" allowfullscreen style="border: 1px solid #e4e4e4;border-radius: 4px;" frameborder="0"></iframe>

**Persamaan:**

$
\begin{cases}
x + y &= 5 \\
2x - y &= 1
\end{cases}
$

Pada grafik, masing-masing persamaan membentuk garis lurus. Karena gradien kedua garis berbeda, grafik menunjukkan bahwa keduanya berpotongan di satu titik. Titik perpotongan tersebut adalah solusi sistem.

Titik potong (2,3) adalah satu-satunya titik yang memenuhi kedua persamaan. Maka sistem memiliki solusi tunggal.

### 2. Solusi Tak Hingga (Membentuk bidang)

<iframe src="https://www.geogebra.org/calculator/aynkdqmc?embed" width="800" height="600" allowfullscreen style="border: 1px solid #e4e4e4;border-radius: 4px;" frameborder="0"></iframe>

**Persamaan:**

$
\begin{cases}
x + y + z &= 4 \\
2x + 3y + z &= 9 \\
3x + 4y + 2z &= 13
\end{cases}
$

Dalam ruang 3D, setiap persamaan membentuk bidang. Pada visualisasi:
- Ketiga bidang tidak sejajar.
- Ketiganya tidak bertemu di satu titik.
- Mereka berpotongan membentuk sebuah garis yang sama

Visualisasinya menunjukkan bidang-bidang beririsan sepanjang garis, bukan titik.
Jika grafik bidang berpotongan membentuk garis, maka sistem memiliki tak hingga solusi.

### 3. Tidak Ada Solusi (Garis Sejajar)

<iframe src="https://www.geogebra.org/calculator/xfh97rgh?embed" width="800" height="600" allowfullscreen style="border: 1px solid #e4e4e4;border-radius: 4px;" frameborder="0"></iframe>

**Persamaan:**

$
\begin{cases}
x + y = 2 \\
x + y = 5
\end{cases}
$

Kedua persamaan memiliki bentuk sama tetapi konstanta berbeda.
Grafik menunjukkan dua garis sejajar dan tidak pernah bertemu.
Karena tidak ada titik potong, tidak ada pasangan (𝑥,𝑦) yang memenuhi kedua persamaan sekaligus. Maka sistem memiliki tidak ada solusi.

_terima kasih_