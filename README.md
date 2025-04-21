---

###nry genshin api

Web API untuk genshin-db menggunakan Vercel serverless function.

Kamu dapat mengakses data gaya v4 dengan mengganti /v5 menjadi /v4.


---

[folder]?query=[query]

Contoh:

https://nry-api.vercel.app/api/v5/characters?query=hutao

Mengembalikan hasil pencarian berdasarkan folder dan query yang diberikan.
Untuk statistik karakter, talenta, atau senjata, gunakan endpoint /stats.

Parameter opsional (case-sensitive):

dumpResult - Mengembalikan objek dengan properti: { query, folder, match, matchtype, options, filename, result }

matchNames - Mencocokkan nama karakter

matchAltNames - Mencocokkan nama alternatif/kustom

matchAliases - Mencocokkan alias

matchCategories - Jika true, mengembalikan array kategori jika cocok

verboseCategories - Jika true, menggantikan string dalam array kategori dengan objek data

queryLanguages - Bahasa pencarian, pisahkan dengan koma

resultLanguage - Bahasa hasil yang diinginkan


Contoh lain:

https://nry-api.vercel.app/api/v5/characters?query=胡桃&queryLanguages=chinese&resultLanguage=chinese
https://nry-api.vercel.app/api/v5/weapons?query=skywardharp&dumpResult=true&resultLanguage=korean


---

[folder]?query=names&matchCategories=true

https://nry-api.vercel.app/api/v5/characters?query=names&matchCategories=true

Mengembalikan daftar nama dalam folder tersebut.
Tambahkan verboseCategories=true untuk mengembalikan objek data, bukan hanya nama.


---

/config

https://nry-api.vercel.app/api/v5/config

Mengembalikan:

Daftar folder

Daftar bahasa

Opsi default

Nilai kategori setiap folder


Gunakan resultLanguage untuk melihat hasil dalam bahasa tertentu:

https://nry-api.vercel.app/api/v5/config?resultLanguage=spanish


---

/folders

https://nry-api.vercel.app/api/v5/folders

Mengembalikan daftar semua folder yang tersedia.


---

/languages

https://nry-api.vercel.app/api/v5/languages

Mengembalikan daftar bahasa yang didukung.


---

/categories

https://nry-api.vercel.app/api/v5/categories

Mengembalikan nilai kategori untuk setiap folder.
Tambahkan resultLanguage untuk hasil berbahasa lain.


---

/stats?folder=[folder]&query=[query]

https://nry-api.vercel.app/api/v5/stats?folder=characters&query=hutao

Mengembalikan statistik tiap level untuk karakter/senjata.
Gunakan level untuk hasil level tertentu (misal: level=80+).
Tambahkan dumpResult=true untuk mendapatkan objek datanya.

Contoh lainnya:

https://nry-api.vercel.app/api/v5/stats?folder=characters&query=ganyu&level=60+
https://nry-api.vercel.app/api/v5/stats?folder=weapons&query=jadespear&level=90


---

/tcgdeckshare/decode?code=[deckcode]

https://nry-api.vercel.app/api/tcgdeckshare/decode?code=A0Bw8TQPARBw8pcPCSBw9cIPDFAg9sgQDAGAAMkQDCGQCdkQDaGQC+MQDrEwDOQQDsAA

Mengubah deckcode TCG menjadi array ID kartu.

Hasil:

{
  "deckcode": "A0Bw8TQPAR..."
}


---

/tcgdeckshare/encode?deck=[cardids]

https://nry-api.vercel.app/api/tcgdeckshare/encode?deck=55,52,23,...

Mengubah array ID kartu menjadi kode deck TCG.
Gunakan offset jika kode mengandung kata yang diblokir:

https://nry-api.vercel.app/api/tcgdeckshare/encode?offset=1&deck=55,52,23,...


---

/tcgdeckshare/getdata?code=[deckcode]&deck=[cardids]

Untuk mendapatkan data gabungan berdasarkan deckcode dan ID kartu.


---