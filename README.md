# Bilangan fibonacci

### Nama           : Ihsan Hadimulya ###
### NIM            : 312210047 ###
### Kelas          : TI.22.A1 ### 
### Dosen Pengampu : Donny Maulana S.Kom., M.M.S.I

# Tugas Pertemuan 6
![SS Tugas P6](https://github.com/SANEXP04/fibonacci/assets/115678077/fd7ce53b-b7eb-4bb6-aead-1d54c252b543)


## DAFTAR ISI <br>
| No | Description | Link |
|-----|------|-----|
|1|layout|[Click Here](#layout)|
|2|String|[Click Here](#string)|
|3|java|[Click Here](#java)|
|4|video|[Click Here](#video)|

## layout 
Pada layout terdapat 3 button yang berfungsi yang memiliki fungsi yang berbeda terdapat button Count "Yaitu untuk menambah angka pada bilangan fibbonaci"<br>
Lalu ada Toast pada button Toast"berfungsi untuk merestart angka atau mengatur ulang angka"<br>
Dan satu lagi ada button berapa angka limit yang ingin dimasukan"ya fungsinya sudah sangat jelas karena saya menulis keterangan pada button seperti itu ,itu berungsi untuk mengatur jumlah limit<br>

<h4>Berikut codingannya</h4>

    <?xml version="1.0" encoding="utf-8"?>
    <androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button_limit"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:background="@color/colorPrimary"
        android:onClick="setLimit"
        android:textColor="@android:color/white"
        android:text="@string/enter_fibonacci_limit"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize"/>


    <Button
        android:id="@+id/button_count"
        android:layout_width="190dp"
        android:layout_height="48dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_finish"
        android:layout_width="190dp"
        android:layout_height="48dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="@color/colorPrimary"
        android:onClick="back1"
        android:text="@string/button_label_finish"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="#7D0552  "
        android:gravity="center_vertical"
        android:text="@string/count_initial_value"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_limit"
        tools:ignore="RtlCompat" />
    
    </androidx.constraintlayout.widget.ConstraintLayout>
      
      
## string
String disini akan dipanggil untuk activity_main yang sudah dibuat terdapat beberapa string yang sudah saya buat disini

            <resources>
    <string name="app_name">Fibonacci</string>
    <string name="button_label_count">COUNT</string>
    <string name="count_initial_value">1</string>
    <string name="button_label_finish">RESET</string>
    <string name="enter_fibonacci_limit">Masukan Limit Angka Yang Anda Inginkan!</string>
           </resources>



## java 
Java disini berfungsi untuk mengatur sistem pop up(atau tombol button ketika ditekan/di klik) yang ada terdapat di tampilan activity_main

package com.fibonacci;

import android.app.AlertDialog;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private TextView showCount;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 0;
    private int limit = -1; // Inisialisasi limit dengan nilai default


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        showCount = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            showCount.setText("0");
        } else if (count == 1) {
            showCount.setText("1");
        } else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limibonacciit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                showCount.setText(getString(R.string.count_initial_value));
            } else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                // Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.color1; // Warna default
                switch (count % 3) {
                    case 1:
                        colorResId = R.color.color1; // Warna merah
                        break;
                    case 2:
                        colorResId = R.color.color2; // Warna hijau
                        break;
                    case 0:
                        colorResId = R.color.color3; // Warna biru
                        break;
                }
                showCount.setTextColor(getResources().getColor(colorResId));
                showCount.setText(String.valueOf(fibCurrent));
            }
        }

        count++;
    }

    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        limit = -1;
        showCount.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set limit bilangan yang ditampilkan :");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", (dialog, which) -> {
            String limitStr = input.getText().toString();
            limit = Integer.parseInt(limitStr);
        });

        builder.setNegativeButton("Cancel", (dialog, which) -> dialog.cancel());

        builder.show();
    }
}


Dan berikut video tampilan sistem Fibonacci nya yang dijalankan melalui Handphone
## video

https://github.com/SANEXP04/fibonacci/assets/115678077/d2e3fc31-1238-44a7-bf29-055774d94eb5

