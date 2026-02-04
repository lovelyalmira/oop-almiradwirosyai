# oop-almiradwirosyai

# Latihan 1: Membuat Class Hero
<img width="901" height="657" alt="image" src="https://github.com/user-attachments/assets/f95e92be-5793-443d-b441-50323d446b2b" />

output dari code di atas :

<img width="775" height="274" alt="image" src="https://github.com/user-attachments/assets/ebafe440-11ae-4605-90d1-8ec498a366e6" />


# Latihan 2: Interaksi Antar Objek (Method) 
<img width="796" height="785" alt="image" src="https://github.com/user-attachments/assets/e0eae193-880f-4ea0-859e-c5e631dff180" />

# Output Pertarungan

<img width="493" height="180" alt="image" src="https://github.com/user-attachments/assets/f19e2243-df7b-4ed2-a712-559b5b937850" />


# Tugas Analisis 2:
 “Perhatikan parameter lawan pada method serang. Parameter tersebut  menerima sebuah objek utuh, bukan hanya string nama. Mengapa ini  penting?“
Parameter lawan pada method serang harus menerima objek utuh, bukan hanya string nama, karena objek memiliki atribut dan method yang dibutuhkan dalam pertarungan. 

# Latihan 3: Pewarisan (Inheritance)
<img width="594" height="716" alt="image" src="https://github.com/user-attachments/assets/5900231c-4b21-4b6c-bf23-2eecae8580b2" />


output dari code di atas :

<img width="570" height="190" alt="image" src="https://github.com/user-attachments/assets/917e0ee6-3bef-44f7-99af-08e12862e03d" />


# Tugas Analisis 3 :
1.
<img width="817" height="205" alt="image" src="https://github.com/user-attachments/assets/65ac071b-98e9-43b8-8112-7cfe3fd8f2e8" />

2. Error tetap muncul meskipun nama “Eudora” sudah dituliskan karena constructor milik class Hero tidak dijalankan. Akibatnya atribut name tidak pernah dibuat pada objek Mage. Saat method info() mencoba mengakses self.name, program tidak menemukannya sehingga terjadi error.

3. super() berfungsi untuk mengambil dan menjalankan constructor milik class Induk (Hero) agar data dari Hero bisa dipakai oleh Mage.
   
# Latihan 4: Enkapsulasi (Mengamankan Data HP) 
<img width="539" height="632" alt="image" src="https://github.com/user-attachments/assets/6b5ac4e1-5e9d-49f7-8a08-e69f5ac515b5" />

output dari code di atas :

<img width="593" height="81" alt="image" src="https://github.com/user-attachments/assets/94d65650-ecbc-43a9-b11a-0756f621e88c" />

# 1. Melanggar Kontrak
Error yang muncul:
 Error yang muncul adalah:
TypeError: Can't instantiate abstract class Hero with abstract method serang
Penjelasan:
 Pesan error tersebut berarti class Hero merupakan abstract class yang memiliki abstract method bernama serang. Ketika method serang dihapus atau tidak dibuat, maka class Hero dianggap belum lengkap. Oleh karena itu, Python tidak mengizinkan pembuatan objek dari class tersebut.
Konsekuensi jika lupa membuat method yang dijanjikan di Interface:
 Jika method yang telah didefinisikan di interface atau abstract class tidak diimplementasikan, maka:
A. Program akan mengalami error saat dijalankan
B. Class tidak dapat diinstansiasi menjadi objek
C. Class tersebut tidak dapat digunakan dalam program
Hal ini terjadi karena abstract class berfungsi sebagai kontrak yang wajib dipenuhi oleh class itu sendiri atau class turunannya.
2. Mencetak Cetakan
Alasan class GameUnit tidak dapat dibuat menjadi objek:
 Class GameUnit tidak dapat dibuat menjadi objek karena merupakan abstract class. Abstract class biasanya masih memiliki method abstrak sehingga belum memiliki perilaku yang lengkap untuk dijalankan.
Fungsi class GameUnit:
 Meskipun tidak dapat dibuat menjadi objek, class GameUnit memiliki fungsi sebagai:
1. Cetakan atau kerangka dasar (blueprint)
2. Penentu struktur dan aturan umum bagi class turunannya
3. Penjamin bahwa semua class turunan memiliki method yang sama
   Class GameUnit digunakan sebagai dasar bagi class lain seperti Hero atau Monster, sehingga membantu menjaga konsistensi dan keteraturan dalam program.

# Tugas Analisis 6:

<img width="556" height="812" alt="image" src="https://github.com/user-attachments/assets/cdab0e18-178d-4ff0-ba3e-c3440bf566fa" />

hasil code di atas :

<img width="450" height="325" alt="image" src="https://github.com/user-attachments/assets/4638c91c-8c0c-4b71-8467-dcff21e03605" />

 
# 1. Uji Skalabilitas (Kemudahan Menambah Fitur)
Setelah menambahkan class baru Healer(Hero) tanpa mengubah kode pada bagian looping (for pahlawan in pasukan:) dan memasukkan objek Healer ke dalam list pasukan, program tetap berjalan dengan lancar. Method serang() pada objek Healer tetap dapat dipanggil sesuai dengan implementasi yang dibuat pada class tersebut.
Kesimpulan:
 Polimorfisme memberikan keuntungan besar bagi programmer karena memungkinkan penambahan karakter atau fitur baru tanpa perlu mengubah kode yang sudah ada, khususnya pada bagian yang menggunakan looping atau pemanggilan method. Hal ini membuat program:
A. Lebih mudah dikembangkan (scalable)
B. Lebih fleksibel
C. Lebih aman dari kesalahan akibat perubahan kode lama
   Dalam pengembangan game, polimorfisme memudahkan penambahan karakter baru di masa depan tanpa merusak sistem yang telah berjalan.
   
3. Konsistensi Penamaan Method
Ketika nama method serang pada class Archer diubah menjadi tembak_panah, program akan mengalami error saat dijalankan.
Penjelasan:
 Error terjadi karena pada bagian looping, program memanggil method serang() untuk setiap objek di dalam list pasukan. Namun, objek Archer tidak lagi memiliki method bernama serang, sehingga Python tidak dapat menemukan method tersebut.

D. Tugas Proyek Integrasi (Challenge)
<img width="705" height="913" alt="image" src="https://github.com/user-attachments/assets/f9f53782-41a7-4d76-842b-bdf48c60dbb3" />

<img width="637" height="859" alt="image" src="https://github.com/user-attachments/assets/5975a3da-0341-497c-af51-28104e370415" />

# hasi code nya : 

<img width="360" height="223" alt="image" src="https://github.com/user-attachments/assets/ea351996-afd4-4fb3-86ca-c6b46351c94b" />


