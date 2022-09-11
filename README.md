# Text-Preprocessing
Stopword &amp; Stemming using Python Sastrawi


Sastrawi Python is a simple python library which allows you to reduce inflected words in Indonesian Language (Bahasa Indonesia) to their base form (stem). This is Python port of the original Sastrawi project written in PHP (credits goes to the original author and contributors of Sastrawi PHP).

# 1. install Sastrawi
jalankan `pip install PySastrawi` di  Jupyter Notebook

# 2. Melihat kamus stopword pada python sastrawi
```
from Sastrawi.StopWordRemover.StopWordRemoverFactory import StopWordRemoverFactory

factory = StopWordRemoverFactory()
stopwords = factory.get_stop_words()

print(stopwords)
```
# 3. Melakukan stopword removal atau menghilangkan kata-kata dalam sebuah kalimay yang tidak memiliki makna
```
from Sastrawi.StopWordRemover.StopWordRemoverFactory import StopWordRemoverFactory

factory = StopWordRemoverFactory()
stopword = factory.create_stop_word_remover()

kalimat = 'Kita tidak bisa menyangkal, bahwa dengan berkembangnya teknologi menjadi semakin canggih banyak hal di sekitar kita yang menggunakan program komputer. Anda bisa lihat program komputer ini disematkan pada smartphone, mobil dan lain-lain.Seiring berjalannya waktu tentu kita membutuhkan program-program baru yang sebisa mungkin memudahkan hidup manusia. Oleh karena itu banyak sekali programmer yang berkreasi dan berinovasi menciptakan program paling baru yang akan bermanfaat untuk manusia.Menjadi seorang programmer yang mahir menciptakan program-program komputer yang bermanfaat dan menguntungkan tidaklah mudah. Banyak proses belajar dan praktik yang harus dilalui agar bisa menjadi programmer yang handal.
```
# 4. Mengubah semua huruf dalam paragraf menjadi huruf kecil
```
kalimat = kalimat.lower()

stop = stopword.remove(kalimat)
print(stop)`
```
# 5.Menambah kamus stopword yang belum ada di python sastrawi
```
from Sastrawi.StopWordRemover.StopWordRemoverFactory import StopWordRemoverFactory, StopWordRemover, ArrayDictionary

kalimat = 'tidak menyangkal, dengan berkembangnya teknologi menjadi semakin canggih banyak di kita menggunakan program komputer. bisa lihat program komputer disematkan smartphone, mobil lain-lain.seiring berjalannya waktu kita membutuhkan program-program baru sebisa mungkin memudahkan hidup manusia. karena banyak sekali programmer berkreasi berinovasi menciptakan program paling baru akan bermanfaat manusia.menjadi seorang programmer mahir menciptakan program-program komputer bermanfaat menguntungkan tidaklah mudah. banyak proses belajar praktik harus dilalui bisa menjadi programmer handal.'

stop_factory = StopWordRemoverFactory().get_stop_words()
more_stopword = ['ada', 'sesuai', 'maupun', 'banyak', 'sebagai']

data = stop_factory + more_stopword

dictionary = ArrayDictionary(data)
str = StopWordRemover(dictionary)

print(str.remove(kalimat))
```
# 6.Melakukan stemming untuk mengubah kata imbuhan menjadi kata dasar
```
from Sastrawi.Stemmer.StemmerFactory import StemmerFactory

factory = StemmerFactory()
stemmer = factory.create_stemmer()

kalimat = 'menyangkal, berkembangnya teknologi menjadi semakin canggih di menggunakan program komputer. lihat program komputer disematkan smartphone, mobil lain-lain.seiring berjalannya waktu membutuhkan program-program baru sebisa mungkin memudahkan hidup manusia. sekali programmer berkreasi berinovasi menciptakan program paling baru bermanfaat manusia.menjadi seorang programmer mahir menciptakan program-program komputer bermanfaat menguntungkan tidaklah mudah. banyak proses belajar praktik dilalui menjadi programmer handal.'

output = stemmer.stem(kalimat)
```
# 7.kata berimbuhan akan berubah menjadi kata dasar dan karakter atau tanda baca akan hilang
```
print(output)
```
