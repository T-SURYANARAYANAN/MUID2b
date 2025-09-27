# Ex.No:2b To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
Start app → show first screen.

User enters a number in the box.

User presses the Factorial button.

Read the number from the box.

Send this number to the second screen using explicit intent.

Open the second screen.

Second screen receives the number.

Calculate factorial of the number.

Show the factorial result in a TextView.

End.

## PROGRAM:

Program to implement ExplicitIntent .<br>
Developed by: SURYANARAYANAN T <br>
Registeration Number :212224040341 <br>
### MainActivity.java
```
package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity
{

    EditText numberInput;
    Button factorialBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        numberInput = findViewById(R.id.editTextNumber);
        factorialBtn = findViewById(R.id.buttonFactorial);

        factorialBtn.setOnClickListener(new View.OnClickListener()
        {
            @Override
            public void onClick(View v)
            {
                String numStr = numberInput.getText().toString();
                if (!numStr.isEmpty())
                {
                    int number = Integer.parseInt(numStr);
                    Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                    intent.putExtra("number", number);
                    startActivity(intent);
                }
            }
        });
    }
}

```
### MainActivity2.java
```
package com.example.explicitintent;

import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity
{

    TextView resultView;

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        resultView = findViewById(R.id.textViewResult);
        int number = getIntent().getIntExtra("number", 0);
        long fact = factorial(number);
        resultView.setText("Factorial of " + number + " = " + fact);
    }
    private long factorial(int n)
    {
        long result = 1;
        for (int i = 1; i <= n; i++)
        {
            result *= i;
        }
        return result;
    }
}
```
### activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editTextNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter a number"
        android:inputType="number"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.384" />

    <Button
        android:id="@+id/buttonFactorial"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.527" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="222dp"
        android:layout_height="51dp"
        android:layout_marginStart="116dp"
        android:text="Explicit Intent"
        android:textColor="#233DD3"
        android:textSize="24sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.463" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
### activity_main2.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textViewResult"
        android:layout_width="231dp"
        android:layout_height="65dp"
        android:text="Result will appear here"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="222dp"
        android:layout_height="51dp"
        android:text="Explicit Intent"
        android:textColor="#233DD3"
        android:textSize="24sp"
        app:layout_constraintBottom_toTopOf="@+id/textViewResult"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.582"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.585" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
## OUTPUT
### MainActivity.java
<img width="1920" height="1080" alt="Screenshot 2025-09-27 210840" src="https://github.com/user-attachments/assets/7b029e06-a7d5-4600-9c7a-9445d20e68da" /><br>
### activity_main.xml
<img width="1920" height="1080" alt="Screenshot 2025-09-27 211037" src="https://github.com/user-attachments/assets/558fda33-7dda-49a9-8781-f55f274d95c3" /><br>
### activity_main2.xml
<img width="1920" height="1080" alt="Screenshot 2025-09-27 211046" src="https://github.com/user-attachments/assets/a403d3f7-1743-4fb3-a5a0-25a7deeed0cf" /><br>
### First Screen
<img width="364" height="802" alt="Screenshot 2025-09-27 211543" src="https://github.com/user-attachments/assets/82e784a8-4160-4bb9-96ec-b639670ff8d3" /><br>
### Secod Screen 
<img width="366" height="799" alt="Screenshot 2025-09-27 211613" src="https://github.com/user-attachments/assets/b4418441-d724-4bbc-96fd-eafbf08fc9ba" /><br>

## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


