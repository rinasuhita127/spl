# Mencari invers matriks

$$
A =
\left[
\begin{array}{cccc}
1 & 1 & 1 & 1 \\
2 & -1 & 1 & -1 \\
1 & 2 & -1 & 1 \\
3 & -1 & 2 & 1
\end{array}
\right]
$$


## Hitung determinan A

Rumus ekspansi:

$$
\det(A)=\sum_{j=1}^{n} a_{ij}M_{ij}
$$

dengan

$$
M_{ij}=(-1)^{i+j}M_{ij}
$$

Ekspansi sepanjang baris pertama:

$$
\det(A)=
1
\left|
\begin{array}{ccc}
-1 & 1 & -1\\
2 & -1 & 1\\
-1 & 2 & 1
\end{array}
\right|
-
1
\left|
\begin{array}{ccc}
2 & 1 & -1\\
1 & -1 & 1\\
3 & 2 & 1
\end{array}
\right|
+
1
\left|
\begin{array}{ccc}
2 & -1 & -1\\
1 & 2 & 1\\
3 & -1 & 1
\end{array}
\right|
-
1
\left|
\begin{array}{ccc}
2 & -1 & 1\\
1 & 2 & -1\\
3 & -1 & 2
\end{array}
\right|
$$

Hasil perhitungan:

$$
\det(A)=13
$$

## Menghitung adjoin matriks

$$
adj(A)=
\left[
\begin{array}{cccc}
-3 & 3 & 4 & 2\\
9 & 4 & 1 & -6\\
11 & 2 & -6 & -3\\
-4 & -9 & 1 & 7
\end{array}
\right]
$$

## Invers matriks

Rumus:

$$
A^{-1}=\frac{1}{\det(A)}adj(A)
$$

Sehingga:

$$
A^{-1}=
\frac{1}{13}
\left[
\begin{array}{cccc}
-3 & 3 & 4 & 2\\
9 & 4 & 1 & -6\\
11 & 2 & -6 & -3\\
-4 & -9 & 1 & 7
\end{array}
\right]
$$

## Invers dalam bentuk pecahan

$$
A^{-1}=
\left[
\begin{array}{cccc}
-\frac{3}{13} & \frac{3}{13} & \frac{4}{13} & \frac{2}{13}\\
\frac{9}{13} & \frac{4}{13} & \frac{1}{13} & -\frac{6}{13}\\
\frac{11}{13} & \frac{2}{13} & -\frac{6}{13} & -\frac{3}{13}\\
-\frac{4}{13} & -\frac{9}{13} & \frac{1}{13} & \frac{7}{13}
\end{array}
\right]
$$