# oop-almiradwirosyai

Latihan 1: Membuat Class Hero

#class Hero:
     Constructor: dijalankan saat Hero baru dibuat
    def __init__(self, name, hp, attack_power):
        self.name = name              # Nama Hero
        self.hp = hp                  # Nyawa (Health Point)
        self.attack_power = attack_power  # Kekuatan Serangan

     Method untuk menampilkan info hero
    def info(self):
        print(f"Hero: {self.name} | HP: {self.hp} | Power: {self.attack_power}")


--- Main Program ---
# Membuat Object (Instansiasi)
hero1 = Hero("Layla", 100, 15)
hero2 = Hero("Zilong", 120, 20)

 Memanggil Method
hero1.info()
hero2.info()

print(hero1.hp)
output dari code di atas :
Hero: Layla | HP: 100 | Power: 15
Hero: Zilong | HP: 120 | Power: 20
100


Latihan 2: Interaksi Antar Objek (Method) 
class Hero:
    # Constructor: dijalankan untuk Hero baru dibuat
    def __init__(self, name, hp, attack_power):
        self.name = name              # nama hero
        self.hp = hp                  # ini nyawa nya
        self.attack_power = attack_power  # serangan

    # Method untuk menampilkan info hero
    def info(self):
        print(f"Hero: {self.name} | HP: {self.hp} | Power: {self.attack_power}")

    # Method menyerang: objek ini menyerang objek lain
    def serang(self, lawan):
        print(f"{self.name} menyerang {lawan.name}!")
        lawan.diserang(self.attack_power)

    # Method diserang: menerima damage
    def diserang(self, damage):
        self.hp -= damage
        print(f"{self.name} terkena damage {damage}. Sisa HP: {self.hp}")


# =====================
# Main Program
# =====================

hero1 = Hero("Layla", 100, 15)
hero2 = Hero("Zilong", 120, 20)

# Menampilkan info awal
hero1.info()
hero2.info()

# Output Pertarungan
print("\n--- Pertarungan Dimulai ---")
hero1.serang(hero2)   # Layla menyerang Zilong
hero2.serang(hero1)   # Zilong membalas

output dari code di atas :
Hero: Layla | HP: 100 | Power: 15
Hero: Zilong | HP: 120 | Power: 20

--- Pertarungan Dimulai ---
Layla menyerang Zilong!
Zilong terkena damage 15. Sisa HP: 105
Zilong menyerang Layla!
Layla terkena damage 20. Sisa HP: 80

Tugas Analisis 2:
 “Perhatikan parameter lawan pada method serang. Parameter tersebut  menerima sebuah objek utuh, bukan hanya string nama. Mengapa ini  penting?“
Parameter lawan pada method serang harus menerima objek utuh, bukan hanya string nama, karena objek memiliki atribut dan method yang dibutuhkan dalam pertarungan. 

Latihan 3: Pewarisan (Inheritance)
class Hero:
    def __init__(self, name, hp, attack_power):
        self.name = name
        self.hp = hp
        self.attack_power = attack_power

    def info(self):
        print(f"Hero: {self.name} | HP: {self.hp} | Power: {self.attack_power}")

    def serang(self, lawan):
        print(f"{self.name} menyerang {lawan.name}!")
        lawan.diserang(self.attack_power)

    def diserang(self, damage):
        self.hp -= damage
        print(f"{self.name} terkena damage {damage}. Sisa HP: {self.hp}")


# =========================
# Class Mage (Inheritance)
# =========================
class Mage(Hero):
    def __init__(self, name, hp, attack_power, mana):
        # Memanggil constructor milik Parent (Hero)
        super().__init__(name, hp, attack_power)
        self.mana = mana

    def info(self):
        print(f"{self.name} [Mage] | HP: {self.hp} | Mana: {self.mana}")

    # Skill khusus Mage
    def skill_fireball(self, lawan):
        if self.mana >= 20:
            print(f"{self.name} menggunakan Fireball ke {lawan.name}!")
            self.mana -= 20
            lawan.diserang(self.attack_power * 2)
        else:
            print(f"{self.name} gagal skill! Mana tidak cukup.")


# =====================
# Main Program
# =====================
print("\n--- Update Class Hero ---")

eudora = Mage("Eudora", 80, 30, 100)
balmond = Hero("Balmond", 200, 10)

eudora.info()
eudora.serang(balmond)        # Serangan biasa (warisan dari Hero)
eudora.skill_fireball(balmond)  # Skill khusus Mage

output dari code di atas :
--- Update Class Hero ---
Eudora [Mage] | HP: 80 | Mana: 100
Eudora menyerang Balmond!
Balmond terkena damage 30. Sisa HP: 170
Eudora menggunakan Fireball ke Balmond!
Balmond terkena damage 60. Sisa HP: 110

Tugas Analisis 3 :
1.
--- Update Class Hero ---
Traceback (most recent call last):
  File "c:\Users\Almira\OneDrive\문서\tugas-oop\game_rpg.py", line 43, in <module>
    eudora.info()
  File "c:\Users\Almira\OneDrive\문서\tugas-oop\game_rpg.py", line 26, in info
    print(f"{self.name} [Mage] | HP: {self.hp} | Mana: {self.mana}")
AttributeError: 'Mage' object has no attribute 'name'

3. Error tetap muncul meskipun nama “Eudora” sudah dituliskan karena constructor milik class Hero tidak dijalankan. Akibatnya atribut name tidak pernah dibuat pada objek Mage. Saat method info() mencoba mengakses self.name, program tidak menemukannya sehingga terjadi error.

4. super() berfungsi untuk mengambil dan menjalankan constructor milik class Induk (Hero) agar data dari Hero bisa dipakai oleh Mage.
class Hero:
    def __init__(self, nama, hp_awal):
        self.nama = nama
        # Enkapsulasi: HP bersifat private
        self.__hp = hp_awal

    # GETTER: melihat HP
    def get_hp(self):
        return self.__hp

    # SETTER: mengubah HP dengan aturan
    def set_hp(self, nilai_baru):
        if nilai_baru < 0:
            self.__hp = 0
        elif nilai_baru > 1000:
            print("Cheat terdeteksi! HP dimaksimalkan ke 1000 saja.")
            self.__hp = 1000
        else:
            self.__hp = nilai_baru

    def diserang(self, damage):
        sisa_hp = self.get_hp() - damage
        self.set_hp(sisa_hp)
        print(f"{self.nama} terkena damage {damage}. Sisa HP: {self.get_hp()}")

# -- Uji Coba --
hero1 = Hero("Layla", 100)

# hero1.__hp = 9999    # Tidak mengubah HP asli (gagal)
# print(hero1.__hp)    # Error

hero1.set_hp(-50)      # Coba set HP negatif
print(hero1.get_hp())

Latihan 4: Enkapsulasi (Mengamankan Data HP) 
class Hero:
    def __init__(self, nama, hp_awal):
        self.nama = nama
        # Enkapsulasi: HP bersifat private
        self.__hp = hp_awal

    # GETTER: melihat HP
    def get_hp(self):
        return self.__hp

    # SETTER: mengubah HP dengan aturan
    def set_hp(self, nilai_baru):
        if nilai_baru < 0:
            self.__hp = 0
        elif nilai_baru > 1000:
            print("Cheat terdeteksi! HP dimaksimalkan ke 1000 saja.")
            self.__hp = 1000
        else:
            self.__hp = nilai_baru

    def diserang(self, damage):
        sisa_hp = self.get_hp() - damage
        self.set_hp(sisa_hp)
        print(f"{self.nama} terkena damage {damage}. Sisa HP: {self.get_hp()}")

# -- Uji Coba --
hero1 = Hero("Layla", 100)

# hero1.__hp = 9999    # Tidak mengubah HP asli (gagal)
# print(hero1.__hp)    # Error

hero1.set_hp(-50)      # Coba set HP negatif
print(hero1.get_hp())

output dari code di atas :
0

1. Melanggar Kontrak
Error yang muncul:
 Error yang muncul adalah:
TypeError: Can't instantiate abstract class Hero with abstract method serang
Penjelasan:
 Pesan error tersebut berarti class Hero merupakan abstract class yang memiliki abstract method bernama serang. Ketika method serang dihapus atau tidak dibuat, maka class Hero dianggap belum lengkap. Oleh karena itu, Python tidak mengizinkan pembuatan objek dari class tersebut.
Konsekuensi jika lupa membuat method yang dijanjikan di Interface:
 Jika method yang telah didefinisikan di interface atau abstract class tidak diimplementasikan, maka:
Program akan mengalami error saat dijalankan


Class tidak dapat diinstansiasi menjadi objek


Class tersebut tidak dapat digunakan dalam program


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

Tugas Analisis 6:

# Parent Class
class Hero:
    def __init__(self, nama):
        self.nama = nama

    def serang(self):
        print("Hero menyerang dengan tangan kosong.")


# Child Class 1
class Mage(Hero):
    def serang(self):
        print(f"{self.nama} (Mage) menembakkan Bola Api! Boom!")


# Child Class 2
class Archer(Hero):
    def serang(self):
        print(f"{self.nama} (Archer) memanah dari jauh! Jleb!")


# Child Class 3
class Fighter(Hero):
    def serang(self):
        print(f"{self.nama} (Fighter) memukul dengan pedang! Slash!")


# Child Class 4 (Tambahan)
class Healer(Hero):
    def serang(self):
        print(f"{self.nama} tidak menyerang, tapi menyembuhkan teman!")


# -- Penerapan Polymorphism --
pasukan = [
    Mage("Eudora"),
    Archer("Miya"),
    Fighter("Zilong"),
    Mage("Gord"),
    Healer("Estes")
]

print("--- PERANG DIMULAI ---")

# Kode looping TIDAK diubah
for pahlawan in pasukan:
    pahlawan.serang()

hasil code di atas :

--- PERANG DIMULAI ---
Eudora (Mage) menembakkan Bola Api! Boom!
Miya (Archer) memanah dari jauh! Jleb!
Zilong (Fighter) memukul dengan pedang! Slash!
Gord (Mage) menembakkan Bola Api! Boom!
Estes tidak menyerang, tapi menyembuhkan teman!

 
1. Uji Skalabilitas (Kemudahan Menambah Fitur)
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
from abc import ABC, abstractmethod
# ===============================
# ABSTRACT CLASS (Abstraction)
# ===============================
class BarangElektronik(ABC):
    def __init__(self, nama, harga_dasar):
        self.nama = nama
        self.__stok = 0                  # private
        self.__harga_dasar = harga_dasar # private


    # GETTER stok
    def get_stok(self):
        return self.__stok


    # GETTER harga dasar (dipakai anak)
    def _get_harga_dasar(self):
        return self.__harga_dasar


    # SETTER / method ubah stok
    def tambah_stok(self, jumlah):
        if jumlah < 0:
            print(f"Gagal update stok {self.nama}! Stok tidak boleh negatif ({jumlah}).")
        else:
            self.__stok += jumlah
            print(f"Berhasil menambahkan stok {self.nama}: {jumlah} unit.")


    @abstractmethod
    def tampilkan_detail(self):
        pass


    @abstractmethod
    def hitung_harga_total(self, jumlah):
        pass




# ===============================
# CHILD CLASS 1 (Inheritance)
# ===============================
class Laptop(BarangElektronik):
    def __init__(self, nama, harga_dasar, processor):
        super().__init__(nama, harga_dasar)
        self.processor = processor


    def tampilkan_detail(self):
        harga = self._get_harga_dasar()
        pajak = int(harga * 0.10)
        print(f"[LAPTOP] {self.nama} | Proc: {self.processor}")
        print(f"Harga Dasar: Rp {harga:,} | Pajak(10%): Rp {pajak:,}")


    def hitung_harga_total(self, jumlah):
        harga = self._get_harga_dasar()
        pajak = harga * 0.10
        return (harga + pajak) * jumlah




# ===============================
# CHILD CLASS 2 (Inheritance)
# ===============================
class Smartphone(BarangElektronik):
    def __init__(self, nama, harga_dasar, kamera):
        super().__init__(nama, harga_dasar)
        self.kamera = kamera


    def tampilkan_detail(self):
        harga = self._get_harga_dasar()
        pajak = int(harga * 0.05)
        print(f"[SMARTPHONE] {self.nama} | Cam: {self.kamera}")
        print(f"Harga Dasar: Rp {harga:,} | Pajak(5%): Rp {pajak:,}")


    def hitung_harga_total(self, jumlah):
        harga = self._get_harga_dasar()
        pajak = harga * 0.05
        return (harga + pajak) * jumlah




# ===============================
# POLYMORPHISM (Keranjang Belanja)
# ===============================
def proses_transaksi(daftar_barang):
    print("\n--- STRUK TRANSAKSI ---")
    total = 0
    no = 1


    for barang, jumlah in daftar_barang:
        print(f"{no}. ", end="")
        barang.tampilkan_detail()
        subtotal = barang.hitung_harga_total(jumlah)
        print(f"Beli: {jumlah} unit | Subtotal: Rp {int(subtotal):,}\n")
        total += subtotal
        no += 1


    print("----------------------------------------")
    print(f"TOTAL TAGIHAN: Rp {int(total):,}")
    print("----------------------------------------")




# ===============================
# ALUR PROGRAM (User Story)
# ===============================
print("--- SETUP DATA ---")


laptop1 = Laptop("ROG Zephyrus", 20_000_000, "Ryzen 9")
hp1 = Smartphone("iPhone 13", 15_000_000, "12MP")


laptop1.tambah_stok(10)
hp1.tambah_stok(-5)   # harus gagal
hp1.tambah_stok(20)


keranjang = [
    (laptop1, 2),
    (hp1, 1)
]


proses_transaksi(keranjang)



