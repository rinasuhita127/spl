# Penyelesaian Sistem Persamaan Linear Menggunakan Eliminasi Guassian

## A. Sistem Persamaan Linear Tiga Variabel

$$
\begin{cases}
x + y + z = 6 \\
2x + 3y + z = 10 \\
x + 2y + 3z = 13
\end{cases}
$$

**Penyelesaian:**

### 1. Matriks Awal

Kode:

```Python
A = matrix(QQ, [[1, 1, 1, 6],[2, 3, 1, 10],[1, 2, 3, 13]])
A
```
Output:

$$
\left[
\begin{array}{ccc|c}
1 & 1 & 1 & 6 \\
2 & 3 & 1 & 10 \\
1 & 2 & 3 & 13
\end{array}
\right]
$$

### 2. Eliminasi kolom pertama

Menghilangkan angka di bawah pivot pertama agar jadi nol dengan menggunakan **A.add_multiple_of_row** untuk melakukan perkalian kemudian penjumlahan.

- A.add_multiple_of_row(1, 0, -2)
maksudnya : -2 dikali dengan baris 1 kemudian  ditambah dengan baris 2.

- A.add_multiple_of_row(2, 0, -1)
maksudnya : -1 dikali dengan baris 1 kemudian  ditambah dengan baris 3.

Di sini **0 = baris 1** lalu  **1 = baris 2** dan seterusnya.

Kode Perhitungan:

```Python
A = matrix(QQ, [[1, 1, 1, 6],[2, 3, 1, 10],[1, 2, 3, 13]])
A
A.add_multiple_of_row(1, 0, -2) #untuk meng nol kan kolom 1 pada baris 2
A
A.add_multiple_of_row(2, 0, -1) #untuk meng nol kan kolom 1 pada baris 3
A
```

Output:

$$
\left[
\begin{array}{ccc|c}
1 & 1 & 1 & 6 \\
0 & 1 & -1 & -2 \\
0 & 1 & 2 & 7
\end{array}
\right]
$$

### 3. Eliminasi kolom kedua

Lakukan cara yang sama juga untuk eliminasi kolom kedua

Kode perhitungan:

```Python
A = matrix(QQ, [[1, 1, 1, 6],[2, 3, 1, 10],[1, 2, 3, 13]])
A
A.add_multiple_of_row(1, 0, -2) #untuk meng nol kan kolom 1 pada baris 2
A
A.add_multiple_of_row(2, 0, -1) #untuk meng nol kan kolom 1 pada baris 3
A
A.add_multiple_of_row(2, 1, -1) #untuk meng nol kan kolom 2 pada baris 3
A
```

Output:

$$
\left[
\begin{array}{ccc|c}
1 & 1 & 1 & 6 \\
0 & 1 & -1 & -2 \\
0 & 0 & 3 & 9
\end{array}
\right]
$$

Angka di bawah pivot pertama dan kedua sudah nol, jadi tinggal melakukan substitusi.

### 4. Substitusi

Dari baris 3: 

$$
\begin{aligned}
3z= 9 \\
z = 3
\end{aligned}
$$

Baris 2:

$$
\begin{aligned}
y - z = -2 \\
y - 3 = -2 \\
y = 1
\end{aligned}
$$

Baris 1:

$$
\begin{aligned}
x + y + z = 6 \\
x + 1 + 3 = 6 \\
x = 2
\end{aligned}
$$

Solusi:

$$
\begin{aligned}
(x,y,z) = (2,1,3)
\end{aligned}
$$

## B. Sistem Persamaan Linear Empat Variabel

$$
\begin{cases}
x + y + z + w = 10 \\
2x + 3y + z + w = 16 \\
x + 2y + 3z + w = 18 \\
x + y + z + 2w = 13
\end{cases}
$$

**Penyelesaian**

### 1. Matriks Awal

Kode:

```Python
A = matrix(QQ, [[1, 1, 1, 1, 10],[2, 3, 1, 1, 16],[1, 2, 3, 1, 18],[1, 1, 1, 2, 13]])
A
```

Output:

$$
\left[
\begin{array}{cccc|c}
1 & 1 & 1 & 1 & 10 \\
2 & 3 & 1 & 1 & 16 \\
1 & 2 & 3 & 1 & 18 \\
1 & 1 & 1 & 2 & 13
\end{array}
\right]
$$

### 2. Eliminasi Kolom Pertama

Mengubah angka dibawah pivot pertama menjadi nol

Kode Perhitungan:

```Python
A = matrix(QQ, [[1, 1, 1, 1, 10],[2, 3, 1, 1, 16],[1, 2, 3, 1, 18],[1, 1, 1, 2, 13]])
A
A.add_multiple_of_row(1, 0, -2) #untuk meng nol kan kolom 1 pada baris 2
A
A.add_multiple_of_row(2, 0, -1) #untuk meng nol kan kolom 1 pada baris 3
A
A.add_multiple_of_row(3, 0, -1) #untuk meng nol kan kolom 1 pada baris 4
A
```

Output:

$$
\left[
\begin{array}{cccc|c}
1 & 1 & 1 & 1 & 10 \\
0 & 1 & -1 & -1 & -4 \\
0 & 1 & 2 & 0 & 8 \\
0 & 0 & 0 & 1 & 3
\end{array}
\right]
$$

### 3. Eliminasi Kolom Kedua

Mengubah angka dibawah pivot kedua menjadi nol

Kode:

```Python
A = matrix(QQ, [[1, 1, 1, 1, 10],[2, 3, 1, 1, 16],[1, 2, 3, 1, 18],[1, 1, 1, 2, 13]])
A
A.add_multiple_of_row(1, 0, -2) #untuk meng nol kan kolom 1 pada baris 2
A
A.add_multiple_of_row(2, 0, -1) #untuk meng nol kan kolom 1 pada baris 3
A
A.add_multiple_of_row(3, 0, -1) #untuk meng nol kan kolom 1 pada baris 4
A
A.add_multiple_of_row(2, 1, -1) #untuk meng nol kan kolom 2 pada baris 3
A
```

Output:

$$
\left[
\begin{array}{cccc|c}
1 & 1 & 1 & 1 & 10 \\
0 & 1 & -1 & -1 & -4 \\
0 & 0 & 3 & 1 & 12 \\
0 & 0 & 0 & 1 & 3
\end{array}
\right]
$$

### 4. Substistusi

Baris 4:

$$
\begin{aligned}
w = 3
\end{aligned}
$$

Baris 3:

$$
\begin{aligned}
3z + w = 12 \\
3z + 3 = 12 \\
3z = 12 - 3 \\
3z = 9 \\
z = 3
\end{aligned}
$$

Baris 2:

$$
\begin{aligned}
y - z - w = -4 \\
y - 3 - 3 = -4 \\
y = -4 + 6 \\
y = 2
\end{aligned}
$$

Baris 1:

$$
\begin{aligned}
x + y + z + w = 10 \\
x + 2 + 3 + 3 = 10 \\
x = 10 - 8 \\
x = 2
\end{aligned}
$$

Solusi:

$$
\begin{aligned}
(x,y,z,w) = (2,2,3,3)
\end{aligned}
$$

_Sistem persaman linear 3 variabel 4 variabel di atas merupakan jenis solusi tunggal_