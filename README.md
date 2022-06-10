# API Gateway Heksa Insurance x Koota.id
PT Asuransi Heksa Insurance X PT. Aplikasi Cipta Mandiri
___________________________________________________________

### Submit aplication Data
#### URL & Params Required:
##### - Features
  - Sender : **Koota.id**
  - Target API : **Heksa Insurance**
  - Submit Data aplication from **Koota** to **Heksa Insurance** API for product Asuransi Mikro Perisai Diri Ekstra
#

##### - PRODUK
  - Asuransi Mikro Perisai Diri Ekstra
#

##### - Endpoint
  - **PRODUCTION**
```sh
https://heksainsurance.co.id/heksaapi/api/koota/submitsuccessdata
```
  - **DEVELOPMENT**
```sh
http://103.58.146.64/heksaapi/api/koota/submitsuccessdata
```
#

##### - Method : POST
#

##### - Authorization Basic Auth

| Params | Data Type | Mandatory | Length | Description |
|--|--|--|--|--|
|username| [text] | Y |150 |Username untuk basic auth - diberi oleh heksa insurance |
|password|[text] | Y |150 |Password basic auth - diberi oleh heksa insurance |

#
##### - Body Structure

| Params | | Data Type | Mandatory | Length | Description |
|--|--|--|--|--|--|
|MerchantID| | [text] | Y |50 | ID Merchant diberikan oleh Heksa Insurance|
|SessionID| | [text] | Y |50 | Digenerate Oleh Koota.id harus Uniq untuk setiap request|
|WORDS| | [text] | Y |254 | enkripsi kombinasi SessionID+Premium+MerchantID+Sharedkey SharedKey diberikan oleh heksa insurance|
|TransactionDate| |[text] | Y | | format dd/MM/yyyy |
|ProductCode| | [text] | Y |150 | Kode Produk Asuransi diberikan oleh heksa insurance|
|Quantity| | [integer] | Y |5 | Jumlah Pembelian Produk|
|PolicyHolder| |[jsonObject] | Y | | Pemegang Polis |
|| FullName |[text] | Y | 500 | |
|| Email |[text] | Y | 50 | |
|| Phone |[text] | Y | 15 | |
|| KTPNo |[text] | Y | 20 | |
|| DOB |[date] | Y | | Tanggal Lahir format dd/MM/yyyy|
|| BankName |[text] | N | |  Nama Bank Nasabah|
|| BankAccountNo |[text] | N | | No Rekening Bank Nasabah |
#

##### - Result Structure
| Params | | Data Type | Mandatory | Length | Description |
|--|--|--|--|--|--|
| StatusCode |  | [Text] | Y | 4 | "00" = Berhasil, "500" = Gagal |
| StatusMessage |  | [Text] | Y | 100 |  |
| Value |  | [Text] | Y | 1500 | list string object json |
|| PolicyNo | [Text] | Y | 100 | Nomor Polis |
|| PolicyUrl | [Text] | Y | 250 | Url Download Polis |
|| Message | [Text] | Y | 1500 |  |
#

###### Success Response
```sh
{
    "StatusCode": "00",
    "StatusMessage": "submit data berhasil",
    "Value" : 
    [
      {
          "PolicyNo" : "12345678",
          "PolicyUrl" : "https://heksainsurance.co.id/downloadpolicy=12346789",
          "Message" : ""
       },
      {
          "PolicyNo" : "87654321",
          "PolicyUrl" : "https://heksainsurance.co.id/downloadpolicy=87654321",
          "Message" : ""
       }
     ]
}
```
#
###### Failed Response
```sh
{
    "StatusCode": "500",
    "StatusMessage": "There is an error in system",
    "Value" : 
}
```
#

___________________________________________________________

### Check Data
#### URL & Params Required:
##### - Features
  - Sender : **Koota.id**
  - Target API : **Heksa Insurance**
  - End Point untuk mengecek semua transaksi yang sudah di hit ke heksa insurance
#

##### - PRODUK
  - Asuransi Mikro Perisai Diri Ekstra
#

##### - Endpoint
  - **PRODUCTION**
```sh
https://heksainsurance.co.id/heksaapi/api/koota/checkdata
```
  - **DEVELOPMENT**
```sh
http://103.58.146.64/heksaapi/api/koota/checkdata
```
#

##### - Method : POST
#

##### - Authorization Basic Auth

| Params | Data Type | Mandatory | Length | Description |
|--|--|--|--|--|
|username| [text] | Y |150 |Username untuk basic auth - diberi oleh heksa insurance |
|password|[text] | Y |150 |Password basic auth - diberi oleh heksa insurance |

#
##### - Body Structure

| Params | | Data Type | Mandatory | Length | Description |
|--|--|--|--|--|--|
|MerchantID| | [text] | Y |50 | ID Merchant diberikan oleh Heksa Insurance|
|SessionID| | [text] | Y |50 | Digenerate Oleh Koota.id harus Uniq untuk setiap request|
|WORDS| | [text] | Y |254 | enkripsi kombinasi SessionID+Premium+MerchantID+Sharedkey SharedKey diberikan oleh heksa insurance|
|StartDate| |[text] | Y | | format dd/MM/yyyy |
|EndDate| |[text] | Y | | format dd/MM/yyyy |
#

##### - Result Structure
| Params | | Data Type | Mandatory | Length | Description |
|--|--|--|--|--|--|
| StatusCode |  | [Text] | Y | 4 | "00" = Berhasil, "500" = Gagal |
| StatusMessage |  | [Text] | Y | 100 |  |
| Value |  | [Text] | Y | 1500 | List string object json |
|| SessionID | [Text] | Y | 100 | Session ID dari Koota.id akan ditampilkan kembali |
|| ProductCode | | [text] | Y |150 | Kode Produk Asuransi diberikan oleh heksa insurance|
|| PolicyNo | [Text] | Y | 100 | Nomor Polis |
|| TransactionData | [Text] | Y | | format dd/MM/yyyy |
#

###### Success Response
```sh
{
    "StatusCode": "00",
    "StatusMessage": "",
    "Value" : 
    [
      {
          "SessionID" : "f4faa9a4-058d-4ef2-abe4-d583c47e432f",
          "ProductCode" : "XII-11",
          "PolicyNo" : "12345678",
          "TransactionData" : "02/01/2022"
       },
       {
          "SessionID" : "f4faa9a4-058d-4ef2-abe4-d583c47e432f",
          "ProductCode" : "XII-11",
          "PolicyNo" : "12345678",
          "TransactionData" : "02/01/2022"
       }
     ]
}
```
#
###### Failed Response
```sh
{
    "StatusCode": "500",
    "StatusMessage": "There is an error in system",
    "Value" : 
}
```
#

____________________________________________________________________

#### Pernyataan Pekerjaan
Pernyataan dibawah ini merupakan pernyataan kamu/calon tertanggung mengenai persyaratan produk Asuransi Mikro Perisai Diri Ekstra
___________________________________________________________
- Saya/Calon Tertanggung bukanlah Anggota Pasukan Khusus/Elite TNI/POLRI
- Saya/Calon Tertanggung bukanlah Pilot, Pramugari atau Mahasiswa Penerbangan
- Saya/Calon Tertanggung bukanlah pekerja lapangan di Pertambangan, Minyak Bumi dan Gas Alam
- Saya/Calon Tertanggung bukanlah Mekanik Listrik Tegangan Tinggi
- Saya/Calon Tertanggung bukanlah Pembersih kaca jendela ketinggian diatas 50 kaki
- Saya/Calon Tertanggung bukanlah Pekerja yang terpapar zat beracun, radiasi nuklir 
- Saya/Calon Tertanggung bukanlah Pekerja Pelayaran/Pelaut, Nelayan
- [x] Saya setuju dengan kondisi pernyataan di atas
____________________________________________________________________

#### Pernyataan Kesehatan
Pernyataan dibawah ini merupakan pernyataan kamu/calon tertanggung mengenai persyaratan produk HAsuransi Mikro Perisai Diri Ekstra
___________________________________________________________
- Saya/Calon Tertanggung sehat, tidak sedang dirawat di Rumah Sakit
- Saya/Calon Tertanggung tidak  pernah atau sedang menderita salah satu dari penyakit, gejala penyakit / kelainan yang berhubungan dengan : cacat / kelumpuhan, tumor / kanker / kista, TBC atau penyakit paru lainnya, asma, Diabetes, penyakti Hati, penyakit Ginjal, penyakit Jantung, penyakit Jantung bawaan, Stroke / mini stroke, Hipertensi, gangguan jiwa, pencangkokan organ tubuh, HIV / AIDS, penyakit kritis bawaan sejak lahir / kongenital, penyakit darah dan pembuluh darah, penyakit Autoimune dan Kolesterolemia.
- Saya/Calon Tertanggung dalam 2 tahun terakhir tidak pernah didiagnosis dengan penyakit, gangguan atau cedera yang membutuhkan konsultasi yang berkelanjutan, rawat inap atau perawatan medis secara terus menerus selama 7 hari atau lebih (kecuali untuk flu, infeksi saluran pernafasan atau penyakit virus) atau pernah menjalani pembedahan atau menjalani tes medis dengan hasil tidak normal (misalnya : tes darah atau urin, USG, CT scan, MRI, biopsi dll).
- Saya/Calon Tertanggung tidak sedang hamil 
- [x] Saya setuju dengan kondisi pernyataan di atas
____________________________________________________________________

#### Statment Nasabah
___________________________________________________________
- [x] Saya menyatakan bahwa keterangan kesehatan di atas adalah yang sebenarnya dan merupakan bagian yang tidak terpisahkan dari proses permintaan asuransi yang saya ajukan. Apabila pernyataan yang saya berikan tersebut tidak benar, maka PT. Heksa Solution Insurance berhak membatalkan asuransi dan berhak tidak membayar klaim yang dibuat atas dasar permohonan ini dan tidak diwajibkan mengembalikan uang premi yang telah dibayar atas nama saya. Selanjutnya saya memberi kuasa kepada setiap Dokter/Rumah Sakit/Perusahaan Asuransi/Badan Hukum/Perorangan atau Organisasi lainnya, yang mempunyai catatan atau mengetahui keadaan atau kesehatan saya untuk memberitahukan kepada PT. Heksa Solution Insurance atau mereka yang diberi kuasa olehnya, segala keterangan tentang diri dan kesehatan baik semasa saya masih hidup maupun sesudah saya meninggal dunia.
- [x] Saya menyatakan bahwa Penerima Manfaat yang terlampir pada eSPAJ (Surat Permohonan Asuransi Jiwa Digital) telah memenuhi sebagai pihak yang memiliki kepentingan yang dapat diasuransikan (Insurable Interest) dan memiliki bukti yang sah secara hukum untuk membuktikan hubungannya dengan Tertanggung. Apabila ada data dan informasi yang berbeda, dengan ini saya membebaskan PT Heksa Solution Insurance dari segala tuntutan dari pihak manapun.
- [x] Saya menyatakan bahwa semua Pernyataan atau Keterangan yang saya sampaikan telah lengkap, benar dan sesuai. Apabila terdapat Pernyataan atau Keterangan yang tidak sesuai dengan kondisi sebenarnya, baik disengaja maupun tidak, maka PT Heksa Solution Insurance berhak membatalkan polis dan atau tidak berkewajiban untuk menyetujui permohonan asuransi ini.
                                                                
___________________________________________________________

