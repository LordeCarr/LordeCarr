- 👋 Hi, I’m @LordeCarr
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
LordeCarr/LordeCarr is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

# FrameWork
import sqlite3 as sql




import main_işlevler.add_user as func_kayıt
import main_işlevler.remove_user as func_kayıt_sil

class aa():


    def __init__(self,durum):
        self.durum = durum

        self.create_table()
    def create_table(self):
        file = sql.connect("Veriler.db")
        cur = file.cursor()

        cur.execute("CREATE TABLE IF NOT EXISTS Bilgiler(kullanıcı_ad TEXT , şifre TEXT) ")

        file.commit()
        file.close()

    def menü(self):
        while True:
            try:
                self.seçim = int(input("\n\n\tKullanıcı ekle ==> ( 1 )\n\n\tKullanıcı çıkar ==> ( 2 )\n\n\n\n\n\n"))
                a.func_seçim()
            except ValueError:
                print("\n\tLütfen geçerli değerleri giriniz!")
    
    def func_seçim(self):
        if self.seçim == 1:
            func_kayıt.kayıt()
        if self.seçim == 2:
           func_kayıt_sil.kayıt_sil()

a = aa(durum=True)
while a.durum:
    a.menü()
    
    
# append_user.py
    
import sqlite3 as sql


def kayıt():
    
    i_kullanıcı_ad = input("Kullanıcı adını giriniz :")
    i_şifre = input("Şifre giriniz :")

    kontrol(i_kullanıcı_ad,i_şifre)

def kontrol(kullanıcı_ad,şifre):
    file = sql.connect("Veriler.db")
    cur = file.cursor()

    cur.execute("SELECT * FROM Bilgiler  WHERE  kullanıcı_ad='{}' OR şifre='{}' ".format(kullanıcı_ad,şifre))

    göster = cur.fetchall()

    if göster == []:
        cur.execute("INSERT INTO Bilgiler VALUES  ('{}','{}')".format(kullanıcı_ad,şifre))

        file.commit()
        file.close()

        print("Kullanıcı başarıyla eklenmiştir")
    
    else:
        print("Kullanıcı adı veya şifre kullanılmaktadır!")
    
    
# remove_user.py

import sqlite3 as sql



def kayıt_sil():

    kullanıcı_ad = input("Kullanıcı adı giriniz :")
    şifre = input("Şifre giriniz :")

    kontrol(kullanıcı_ad,şifre)

def kontrol(kullanıcı_adı,şifresi):


    file = sql.connect("Veriler.db")
    cur = file.cursor()

    cur.execute("SELECT * FROM Bilgiler WHERE kullanıcı_ad='{}' AND şifre='{}' ".format(kullanıcı_adı,şifresi))

    sil = cur.fetchall()

    if sil == []:
        print("Kullanıcı adı veya şifre hatalı!\n")
    else:
        cur.execute("DELETE FROM Bilgiler WHERE kullanıcı_ad='{}' AND şifre='{}' ".format(kullanıcı_adı,şifresi))

        file.commit()
        file.close()

        print("Kullanıcı başarıyla silinmiştir")
    file.close()
    
    
    


