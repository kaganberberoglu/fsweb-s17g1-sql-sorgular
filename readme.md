# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu
Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar 
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/] (update, delete, drop sorguları iptal edilmiştir).

### Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını altlarına yazın.

1) ÖRNEK SORU: Öğrenci tablosundaki tüm kayıtları listeleyin.

select * from ogrenci;

2) Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.

select ograd Adı, ogrsoyad Soyadı, sinif Sınıfı from ogrenci;

3) Öğrenci tablosundaki kız öğrencileri listeleyin.

select * from ogrenci 
where cinsiyet = 'K';

4) Öğrenci tablosunda kaydı bulunan sınıfların adını her sınıf bir kez görüntülenecek şekilde listeleyiniz

select distinct sinif from ogrenci;

5) Öğrenci tablosunda, 10A sınıfında olan kız öğrencileri listeleyiniz.

select * from ogrenci 
where cinsiyet = 'K' and sinif = '10A';

6) Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz.

select ograd Adı, ogrsoyad Soyadı, sinif Sınıfı from ogrenci 
where sinif = '10B' or sinif = '10A';

7) Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarası olarak listeleyiniz. (as kullanım örneği)

select ograd Adı, ogrsoyad Soyadı, ogrno as OkulNo from ogrenci;

8) Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (concat, as kullanım örneği)

select concat(ograd, ogrsoyad) adsoyad from ogrenci;

9) Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

select * from ogrenci 
where ograd like 'A%';

10) Kitaplar tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.

select kitapadi, sayfasayisi from kitap 
where sayfasayisi between 50 and 200;

11) Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.

select * from ogrenci 
where ograd in ('Fidan', 'İsmail', 'Leyla');

12) Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.

select * from ogrenci 
where ograd like 'A%' or ograd like 'D%' or ograd like 'K%';

13) Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.

select ograd Adı, ogrsoyad Soyadı, sinif Sınıfı, cinsiyet Cinsiyeti from ogrenci 
where (cinsiyet = 'E' && sinif = '9A') || (cinsiyet = 'K' && sinif = '9B');

14) Sınıfı 10A veya 10B olan erkekleri listeleyiniz.

select * from ogrenci 
where sinif in ('10A','10B') and cinsiyet = 'E';

15) Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.

select * from ogrenci 
where dtarih like '1989%';

16) Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.

select * from ogrenci 
where cinsiyet = 'K' && ogrno between 30 and 50;

17) Öğrencileri adına göre sıralayınız (alfabetik).

select * from ogrenci 
order by ograd;

18) Öğrencileri adına, adı aynı olanları da soyadlarına göre sıralayınız.

select * from ogrenci 
order by ograd, ogrsoyad;

19) 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.

select * from ogrenci 
where sinif = '10A'
order by ogrno desc;

20) Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.

select * from ogrenci 
limit 10;

21) Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.

select ograd Adı, ogrsoyad Soyadı, dtarih DoğumTarihi from ogrenci 
limit 10;

22) Sayfa sayısı en fazla olan kitabı listeleyiniz.

select * from kitap 
order by sayfasayisi desc 
limit 1;

23) Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.

select * from ogrenci 
order by dtarih desc 
limit 1;

24) 10A sınıfındaki en yaşlı öğrenciyi listeyin.

select * from ogrenci 
where sinif = '10A' and dtarih = 'null' 
order by dtarih asc 
limit 1;

25) İkinci harfi N olan kitapları listeleyiniz.

select * from kitap 
where kitapadi like ('_N%');

26) Öğrencileri sınıflarına göre gruplayarak listeleyin.

select * from ogrenci 
order by sinif;

27) Öğrencileri her sorgulamada sıralaması farklı olacak şekilde rastgele listeleyin.
[İPUCU: rand() fonksiyonu]

select * from ogrenci 
order by rand();

28) Öğrenci tablosundan Rastgele bir öğrenci seçiniz.

select * from ogrenci 
order by rand() 
limit 1;

29) 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.

select ograd as Adı, ogrsoyad as Soyadı, ogrno as No, sinif as Sınıf from ogrenci 
where sinif = "10A" 
order by rand() 
limit 1;

30) Öğrenci tablosunda aynı isimde kaçar öğrenci olduğunu bulmak istiyoruz.
Öğrenci isimlerinin sayısını "adet" olarak öğrencilerin isimleri "isim" olarak listeleyin.

select ograd as isim, count(*) as adet from ogrenci 
group by ograd;
