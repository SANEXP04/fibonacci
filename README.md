# Bilangan-fibonance_UTS

Nama: Ihsan Hadimulya<br>
Kelas : TI 22.A.1<br>
NIM: 312210047<br>
Matakuliah : Pemrograman Mobile<br>
Dosen pengajar : Donny Maulana, S.Kom., M.M.S.I.

<h3>Assalamualaikum Wr.Wb disini saya akan menampilkan bilangan Fibonacci serta menampilkan codingan yang berfungsi untuk menambah bilangan fibonacci dan merubah warna seiring bertambahnya angka, serta memberikan tombol pop up restart ke angka semula,dan memberikan tombol limit(batasan) berikut adalah daftar isinya :

  
## DAFTAR ISI <br>
| No | Description | Link |
|-----|------|-----|
|1|layout|[Click Here](#layout)|
|2|String|[Click Here](#string)|
|3|java|[Click Here](#java)|
|4|video|[Click Here](#video)|

## layout 
pada layout terdapat 3 button yang berfungsi yang memiliki fungsi yang berbeda terdapat button Count "Yaitu untuk menambah angka pada bilangan fibbonaci"<br>
lalu ada Toast pada button Toast"berfungsi untuk merestart angka atau mengatur ulang angka"<br>
dan satu lagi ada button berapa angka limit yang ingin dimasukan"ya fungsinya sudah sangat jelas karena saya menulis keterangan pada button seperti itu ,itu berungsi untuk mengatur jumlah limit<br>

<h4>berikut codingannya</h4>
          <?xml version="1.0" encoding="utf-8"?>
          <androidx.constraintlayout.widget.ConstraintLayout
          xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:app="http://schemas.android.com/apk/res-auto"
          xmlns:tools="http://schemas.android.com/tools"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          tools:context=".MainActivity">

          <TextView
              android:id="@+id/show_count"
              android:layout_width="0dp"
              android:layout_height="0dp"
              android:layout_marginStart="8dp"
              android:layout_marginTop="8dp"
              android:layout_marginEnd="8dp"
              android:layout_marginBottom="8dp"
              android:background="#87CEFA"
              android:gravity="center_vertical"
              android:text="1"
              android:textAlignment="center"
              android:textColor="@color/ColorPrimary"
              android:textSize="160sp"
              android:textStyle="bold"
              app:layout_constraintBottom_toTopOf="@id/button_count"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintHorizontal_bias="0.0"
              app:layout_constraintStart_toStartOf="parent"
              app:layout_constraintTop_toBottomOf="@id/button_limit"
              app:layout_constraintVertical_bias="1.0"
              tools:ignore="RtlCompat" />  
          <Button
              android:id="@+id/button_limit"
              android:layout_width="0dp"
              android:layout_height="wrap_content"
              android:layout_marginEnd="8dp"
              android:layout_marginStart="8dp"
              android:layout_marginTop="8dp"
              android:background="@color/ColorPrimary"
              android:onClick="setLimit"
              android:textColor="@android:color/white"
              android:text="@string/fibonance_limit"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintStart_toStartOf="parent"
              app:layout_constraintTop_toTopOf="parent"
              tools:ignore="UsingOnClickInXml,VisualLintButtonSize"/>
      
      
          <Button
              android:id="@+id/button_count"
              android:layout_width="389dp"
              android:layout_height="48dp"
              android:layout_marginStart="8dp"
              android:layout_marginEnd="8dp"
              android:layout_marginBottom="72dp"
              android:background="@color/ColorPrimary"
              android:onClick="countUp"
              android:text="@string/button_label_count"
              android:textColor="@android:color/white"
              app:layout_constraintBottom_toBottomOf="parent"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintHorizontal_bias="0.497"
              app:layout_constraintStart_toStartOf="parent"
              tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />
      
          <Button
              android:id="@+id/button_finish"
              android:layout_width="389dp"
              android:layout_height="48dp"
              android:layout_marginStart="8dp"
              android:layout_marginEnd="8dp"
              android:layout_marginBottom="16dp"
              android:background="@color/ColorPrimary"
              android:onClick="back1"
              android:text="@string/button_label_finish"
              android:textColor="@android:color/white"
              app:layout_constraintBottom_toBottomOf="parent"
              app:layout_constraintEnd_toEndOf="parent"
              app:layout_constraintHorizontal_bias="0.497"
              app:layout_constraintStart_toStartOf="parent"
              tools:ignore="UsingOnClickInXml" />
      
        
    
      </androidx.constraintlayout.widget.ConstraintLayout>
      
      
## string
string disini akan dipanggil untuk activity_main yang sudah dibuat terdapat beberapa string yang sudah saya buat disini

            <resources>
                <string name="app_name">HelloAppA1</string>
                <string name="button_label_finish">Toast</string>
                <string name="button_label_count">Count</string>
                <string name="toast_massage">Bilangan Fibonance</string>
                <string name="fibonance_limit">berapa angka limit yang anda mau?</string>
            </resources>



## java 
java disini berfungsi untuk mengatur sistem pop up(atau tombol button ketika ditekan/di klik) yang ada terdapat di tampilan activity_main

                package com.hello;
                
                import android.app.AlertDialog;
                import android.content.DialogInterface;
                import android.graphics.Color;
                import android.os.Bundle;
                import android.view.View;
                import android.widget.EditText;
                import android.widget.TextView;
                import androidx.appcompat.app.AppCompatActivity;
                
                public class MainActivity extends AppCompatActivity {
                    private TextView showCount;
                    private int count = 1;
                    private long fibNMinus1 = 1;
                    private long fibNMinus2 = 1;
                    private int limit = -1; // Inisialisasi limit dengan nilai default
                
                    @Override
                    protected void onCreate(Bundle savedInstanceState) {
                        super.onCreate(savedInstanceState);
                        setContentView(R.layout.activity_fibonance_main);
                
                        showCount = findViewById(R.id.show_count);
                    }
                
                    public void countUp(View view) {
                        if (count == 0) {
                            showCount.setText("0");
                        } else if (count == 1) {
                            showCount.setText("1");
                        } else {
                            if (limit != -1 && count > limit) {
                                // Jika count melebihi limit, atur ulang perhitungan
                                count = 0;
                                fibNMinus1 = 1;
                                fibNMinus2 = 0;
                                showCount.setText(getString(R.string.count_initial_value));
                            } else {
                                long fibCurrent = fibNMinus1 + fibNMinus2;
                                fibNMinus2 = fibNMinus1;
                                fibNMinus1 = fibCurrent;
                
                                // Mengubah warna teks menjadi warna RGB dengan warna yang berbeda setiap kali angka berubah
                                int red = (int) (Math.random() * 256);
                                int green = (int) (Math.random() * 256);
                                int blue = (int) (Math.random() * 256);
                                showCount.setTextColor(Color.rgb(red, green, blue));
                
                                showCount.setText(String.valueOf(fibCurrent));
                            }
                        }
                
                        count++;
                    }
                
                    public void back1(View view) {
                        count = 1;
                        fibNMinus1 = 1;
                        fibNMinus2 = 0;
                        showCount.setText(getString(R.string.count_initial_value));
                    }
                
                    public void setLimit(View view) {
                        // Create and display a dialog to set the limit
                        AlertDialog.Builder builder = new AlertDialog.Builder(this);
                        builder.setTitle("Set Limit");
                
                        final EditText input = new EditText(this);
                        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
                        builder.setView(input);
                
                        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
                            @Override
                            public void onClick(DialogInterface dialog, int which) {
                                // Get the limit from the input and set it for calculations
                                String limitStr = input.getText().toString();
                                limit = Integer.parseInt(limitStr);
                            }
                        });
                
                        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
                            @Override
                            public void onClick(DialogInterface dialog, int which) {
                                dialog.cancel();
                            }
                        });
                
                
                        builder.show();
                    }
                }


berikut video tampilan sistem Fibonnacinya
## video


https://github.com/lampubohlam/Bilangan-fibonance_UTS/assets/116137169/4cafc6d9-30bb-4041-9e22-385abe1c2242


