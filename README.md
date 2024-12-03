Berikut adalah spesifikasi API untuk endpoint konfirmasi, pembatalan, penyelesaian, dan pengulangan konfirmasi dalam format Markdown:

```markdown
# API Specification

## Authentication

Semua permintaan API harus menyertakan header berikut untuk otentikasi:

- **Header:**
  - `X-Api-Key`: "your secret api key"

---

## Confirm Order
### Deskripsi
Endpoint ini digunakan untuk mengonfirmasi pesanan tertentu.

### **Request:**
- **Method:** `POST`
- **Endpoint:** `/api/orders/{order_id}/confirm`
- **Header:**
  - `Content-Type`: `application/json`
  - `Accept`: `application/json`

### **Response:**
```json
{
  "code": "number",
  "status": "string",
  "data": {
    "orderId": "string, unique",
    "status": "confirmed",
    "updatedAt": "date"
  }
}
```

### Penjelasan untuk FE dan BE
- **Frontend**: Kirim permintaan ini saat pengguna mengonfirmasi pesanan. Tampilkan respons di UI untuk menunjukkan bahwa pesanan telah terkonfirmasi.
- **Backend**: Perbarui status pesanan dalam basis data menjadi "confirmed" dan kirimkan respons yang menyertakan detail pesanan yang diperbarui.

---

## Cancel Order
### Deskripsi
Endpoint ini digunakan untuk membatalkan pesanan.

### **Request:**
- **Method:** `POST`
- **Endpoint:** `/api/orders/{order_id}/cancel`
- **Header:**
  - `Content-Type`: `application/json`
  - `Accept`: `application/json`

### **Response:**
```json
{
  "code": "number",
  "status": "string",
  "data": {
    "orderId": "string, unique",
    "status": "canceled",
    "updatedAt": "date"
  }
}
```

### Penjelasan untuk FE dan BE
- **Frontend**: Tawarkan opsi bagi pengguna untuk membatalkan pesanan, dan kirim permintaan ini saat tindakan dilakukan. Tampilkan status pembatalan di UI.
- **Backend**: Ubah status pesanan dalam basis data menjadi "canceled" dan kembalikan detail pesanan yang dibatalkan dalam respons.

---

## Complete Order
### Deskripsi
Endpoint ini digunakan untuk menandai pesanan sebagai selesai.

### **Request:**
- **Method:** `POST`
- **Endpoint:** `/api/orders/{order_id}/complete`
- **Header:**
  - `Content-Type`: `application/json`
  - `Accept`: `application/json`

### **Response:**
```json
{
  "code": "number",
  "status": "string",
  "data": {
    "orderId": "string, unique",
    "status": "completed",
    "updatedAt": "date"
  }
}
```

### Penjelasan untuk FE dan BE
- **Frontend**: Kirim permintaan ini ketika pengguna menandai pesanan sebagai selesai. Berikan umpan balik di UI untuk mengonfirmasi bahwa pesanan telah selesai.
- **Backend**: Perbarui status dalam basis data menjadi "completed" dan kirimkan detail pesanan yang diperbarui dalam respons.

---

## Re-confirm Order
### Deskripsi
Endpoint ini digunakan untuk mengulang konfirmasi pesanan yang sudah ada.

### **Request:**
- **Method:** `POST`
- **Endpoint:** `/api/orders/{order_id}/reconfirm`
- **Header:**
  - `Content-Type`: `application/json`
  - `Accept`: `application/json`

### **Response:**
```json
{
  "code": "number",
  "status": "string",
  "data": {
    "orderId": "string, unique",
    "status": "reconfirmed",
    "updatedAt": "date"
  }
}
```

### Penjelasan untuk FE dan BE
- **Frontend**: Siapkan opsi untuk mengulang konfirmasi pesanan. Ketika diklik, kirim permintaan ini dan tampilkan status terkonfirmasi kembali kepada pengguna.
- **Backend**: Perbarui status pesanan dalam basis data menjadi "reconfirmed" dan kembalikan detail pesanan yang diperbarui.

---

## Kesimpulan
Endpoint baru ini menambah fungsionalitas dalam sistem pemesanan. Karena pengelolaan status pesanan adalah bagian penting dari pengalaman pengguna, penting untuk berkomunikasi dengan jelas di antara tim frontend dan backend untuk memastikan semua status terkelola dengan baik.

- **Frontend**: Harus memahami bagaimana dan kapan memanggil setiap endpoint ini berdasarkan interaksi pengguna.
- **Backend**: Harus memproses status yang relevan secara efisien dan mengembalikan respons yang sesuai untuk membantu frontend memberikan pengalaman pengguna yang baik.

Dokumentasi ini menyajikan pedoman dan harapan untuk setiap interaksi yang dapat dilakukan dengan API terkait status pemesanan.
```

### Penjelasan Format Markdown:
- **Struktur**: Dokumen ini disusun dengan jelas menggunakan header yang berbeda untuk memisahkan bagian-bagian, seperti deskripsi, permintaan, respons, dan penjelasan untuk frontend dan backend.
- **Kode JSON**: Respons JSON disertakan dalam blok kode terpisah agar mudah dibaca.
- **Pemisahan dengan Garis Horizontal**: Garis horizontal (`---`) digunakan untuk memisahkan setiap bagian API untuk meningkatkan keterbacaan.
- **Bahasa yang Jelas**: Penjelasan disusun untuk membantu kedua tim (frontend dan backend) memahami konteks dan fungsi setiap endpoint, menciptakan dasar yang kuat untuk kolaborasi.

Dokumen ini akan bermanfaat bagi pengembang FE dan BE untuk memahami dan menggunakan API dengan benar.