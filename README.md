# Лабораторная работа №1. Создание Activity и передача параметров между ними.
* Выполнила: Зинченко Анна
* Язык программирования: Java

# Что делает приложение?
Этот проект демонстрирует простой пример перехода между двумя экранами (Activity) в Android-приложении. 
Чтобы запустить проект можно прочитать "Как собрать проект?"

# Функциональность:
Приложение содержит две Activity:
  * MainActivity: 
    На этом экране находится кнопка "Перейти к Activity 2".
    <div align="left">
  <img src="https://github.com/domosedochka/Laba1/blob/main/Screenshot_2024-10-09-00-48-33-977_com.example.laba1.jpg" width="200" />
</div>
  * SecondActivity:
     На этом экране отображается текст "Переданный параметр: Зинченко", где Зинченко* - это строка, переданная из MainActivity.
<div align="left">
  <img src="https://github.com/domosedochka/Laba1/blob/main/Screenshot_2024-10-09-00-48-40-164_com.example.laba1.jpg" width="200" />
</div>
# Дополнительные сведения:
* Проект использует стандартные компоненты Android: Activity, Intent, Button, TextView.
* Переход между Activity осуществляется с помощью Intent - объекта, который содержит информацию о том, какую Activity нужно запустить.
* Параметр передается с помощью putExtra("Фамилия", "Зинченко"), а затем извлекается в SecondActivity с помощью getIntent().getStringExtra("Фамилия").

# Как запустить:
1. Импортируйте проект: 
  * Загрузите или клонируйте этот репозиторий.
  * Откройте проект в Android Studio.
2. Запустите приложение:
  * Нажмите кнопку "Run" в Android Studio.
  * Выберите эмулятор или устройство для запуска приложения.
3. Нажмите кнопку:
  * На экране MainActivity нажмите кнопку "Перейти к Activity 2".
  * Вы перейдете на экран SecondActivity, где увидите фамилию Зинченко, переданную из MainActivity.

# Код:
* **MainActivity.java:**
```package com.example.laba1;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import com.example.laba1.SecondActivity;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private Button btn1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btn1 = findViewById(R.id.btn1);

        btn1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                intent.putExtra("Фамилия", "Зинченко");
                startActivity(intent);
            }
        });
    }
}
```
* **SecondActivity.java:**
```package com.example.laba1;
import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    private TextView textView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        textView = findViewById(R.id.textView);

        String фамилия = getIntent().getStringExtra("Фамилия");
        textView.setText("Переданный параметр: " + фамилия);
    }


}
```
* **activity_main.xml:**
```<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/btn1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Перейти к Activity 2"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
* **activity_second.xml:**
```<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Переданный параметр: "
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```




