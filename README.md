# 📱 Aplikasi Formulir Input Android 

Aplikasi Android Native sederhana yang mendemonstrasikan penggunaan 
**Input Control**, seperti:
- Input nomor telepon
- Pemilihan tanggal (Date Picker)
- Pemilihan waktu (Time Picker)  
Hasil input langsung ditampilkan secara real-time dalam `TextView`.



## 🎯 Fitur Aplikasi

- 📞 Input nomor telepon menggunakan `EditText`
- 📅 Pilih tanggal menggunakan `DatePickerDialog`
- ⏰ Pilih waktu menggunakan `TimePickerDialog`
- 📋 Tampilkan hasil input ke `TextView`
---
## ⚙️ Teknologi

- Bahasa: **Kotlin**
- Tampilan: **XML (LinearLayout)**
- Android Studio (SDK min 21, target SDK 34)
---
##  Penjelasan Kode
###  activity_main.xml
```kotlin
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp"
    android:background="@android:color/white">
````
UI menggunakan ```LinearLayout``` yang disusun secara vertikal dan semua elemen diposisikan ke tengah

```Logo```
```kotlin
<ImageView
        android:id="@+id/ivLogo"
        android:layout_width="300dp"
        android:layout_height="120dp"
        android:layout_marginBottom="24dp"
        android:layout_gravity="center"
        android:src="@drawable/logo" />
````
Menampilkan logo dan untuk ```android:src="@drawable/logo"``` disesuaikan dengan nama file logo masing-masing

```Judul Halaman```
```kotlin
<TextView
        android:id="@+id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="BIRO JODOH"
        android:textSize="30sp"
        android:textStyle="bold"
        android:gravity="center"
        android:layout_marginBottom="24dp"/>
```
Text view untuk halaman ```BIRO JODOH```

```Input Phone Number```
```kotlin
<EditText
        android:id="@+id/etphone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Masukan Nomor Telepon Calon"
        android:inputType="phone"
        android:layout_marginBottom="16dp"/>
```
Edit Text untuk field ```memasukan nomor telepon```

```Button tanggal```
```kotlin
    <Button
        android:id="@+id/btnDate"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Pilih Tanggal Jadian"/>
```
Button untuk memilih ```tanggal```

```Button waktu```
```kotlin
<Button
        android:id="@+id/btnTime"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Pilih Waktu jadian"
        android:layout_marginTop="8dp"/>
```
Button untuk memilih ```waktu```

```Input waktu```
```kotlin
<TextView
        android:id="@+id/tvDate"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Tanggal Jadian"
        android:textSize="16sp"
        android:paddingTop="24dp"/>
```
```Penutup```
```kotlin
<TextView
        android:id="@+id/tvPenutup"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginBottom="24dp"
        android:gravity="center"
        android:text="SEMOGA LANGGENG"
        android:textColor="#FF0000"
        android:textSize="30sp"
        android:textStyle="bold" />
```
---
### FULL KODE

```kotlin
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp"
    android:background="@android:color/white">


    <!-- Logo -->
    <ImageView
        android:id="@+id/ivLogo"
        android:layout_width="300dp"
        android:layout_height="120dp"
        android:layout_marginBottom="24dp"
        android:layout_gravity="center"
        android:src="@drawable/logo" />

    <!-- Judul Halaman -->
    <TextView
        android:id="@+id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="BIRO JODOH"
        android:textSize="30sp"
        android:textStyle="bold"
        android:gravity="center"
        android:layout_marginBottom="24dp"/>


    <!-- Input Phone Number -->
    <EditText
        android:id="@+id/etphone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Masukan Nomor Telepon Calon"
        android:inputType="phone"
        android:layout_marginBottom="16dp"/>

    <!-- Button untuk pilih tanggal jadian -->
    <Button
        android:id="@+id/btnDate"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Pilih Tanggal Jadian"/>

    <!-- Button untuk pilih waktu jadian-->
    <Button
        android:id="@+id/btnTime"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Pilih Waktu jadian"
        android:layout_marginTop="8dp"/>

    <TextView
        android:id="@+id/tvDate"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Tanggal Jadian"
        android:textSize="16sp"
        android:paddingTop="24dp"/>

    <TextView
        android:id="@+id/tvPenutup"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginBottom="24dp"
        android:gravity="center"
        android:text="SEMOGA LANGGENG"
        android:textColor="#FF0000"
        android:textSize="30sp"
        android:textStyle="bold" />


</LinearLayout>
```
---

### MainActivity.kt
```kotlin
package com.example.project_elearning1

import android.app.DatePickerDialog
import android.app.TimePickerDialog
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import android.widget.*
import java.util.*
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {

    private lateinit var etPhone: EditText
    private lateinit var btnDate: Button
    private lateinit var btnTime: Button
    private lateinit var tvDate: TextView

    private var selectedDate: String = ""
    private var selectedTime: String = ""

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)

        // Inisialisasi Komponen
        etPhone = findViewById(R.id.etphone)
        btnDate = findViewById(R.id.btnDate)
        btnTime = findViewById(R.id.btnTime)
        tvDate = findViewById(R.id.tvDate)

        //listener DatePicker
        btnDate.setOnClickListener {
            val calendar = Calendar.getInstance()
            val year = calendar.get(Calendar.YEAR)
            val month = calendar.get(Calendar.MONTH)
            val day = calendar.get(Calendar.DAY_OF_MONTH)

            val datePicker = DatePickerDialog(this, { _, y, m, d ->
            selectedDate = "$d/${m+1}/$y"
            updateResult()
            }, year, month, day)

            datePicker.show()
        }

        //listener TimePicker
        btnTime.setOnClickListener {
            val calendar = Calendar.getInstance()
            val hour = calendar.get(Calendar.HOUR_OF_DAY)
            val minute = calendar.get(Calendar.MINUTE)

            val timePicker = TimePickerDialog(this, { _, h, m ->
            selectedTime = "$h:$m"
            updateResult()
            }, hour, minute, true)

            timePicker.show()
        }
    }

    private fun updateResult() {
        val phone = etPhone.text.toString()
        val result = "Telepon: $phone\nTanggal: $selectedDate\nWaktu: $selectedTime"
        tvDate.text = result

    }

}
```
---
**Menangani Tombol Pilihan Tanggal**
```kotlin
btnDate.setOnClickListener {
            val calendar = Calendar.getInstance()
            val year = calendar.get(Calendar.YEAR)
            val month = calendar.get(Calendar.MONTH)
            val day = calendar.get(Calendar.DAY_OF_MONTH)

            val datePicker = DatePickerDialog(this, { _, y, m, d ->
            selectedDate = "$d/${m+1}/$y"
            updateResult()
            }, year, month, day)

            datePicker.show()
        }
```
**Penjelasan**
* Menampilkan dialog pemilih tanggal
* Setelah tanggal dipilih, data disimpan di ```selectedDate``` dan ditampilkan

---
**Menangani Tombol pilihan waktu**
```kotlin
btnTime.setOnClickListener {
            val calendar = Calendar.getInstance()
            val hour = calendar.get(Calendar.HOUR_OF_DAY)
            val minute = calendar.get(Calendar.MINUTE)

            val timePicker = TimePickerDialog(this, { _, h, m ->
            selectedTime = "$h:$m"
            updateResult()
            }, hour, minute, true)

            timePicker.show()
        }
```
**Penjelasan**
* Menampilkan dialog pemilih waktu
* Setelah tanggal dipilih, data disimpan di ```selectedDate``` dan ditampilkan

---

## Links

Github https://github.com/IrgiRanggaSaputra/Mobile-Programming

