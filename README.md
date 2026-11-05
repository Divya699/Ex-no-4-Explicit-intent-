# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
```
1.Start the project: Create a new Android project with two Empty Activities (MainActivity and MainActivity2).

2.Design the First Screen: In activity_main.xml, add an EditText to receive the number input and a Button to trigger the calculation.

3.Design the Second Screen: In activity_main2.xml, add a TextView to display the calculated factorial result.

4.Get Input (MainActivity): Inside MainActivity.java, set an OnClickListener on the button to retrieve the entered number from the EditText.

5.Pass Data using Explicit Intent: Create an Intent targeting MainActivity2.class. Attach the entered number to the intent using intent.putExtra(), and start the activity using startActivity(intent).

6.Receive Data (MainActivity2): In MainActivity2.java, use getIntent().getStringExtra() (or getIntExtra()) to retrieve the passed number.

7.Calculate Factorial: Write a loop or recursive function to compute the factorial of the received number.

8.Display Result: Update the TextView in the second activity to show the computed factorial value.

10.Stop: Run and test the application.

```
## PROGRAM:
### Program to print the text “ExplicitIntent”.
### Developed by: DIVYA PRIYA S
### Registeration Number : 212225240037

## MAINACTIVITY.JAVA:
```

package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Get references to UI elements
        final EditText inputField = findViewById(R.id.input_field);
        Button factorialButton = findViewById(R.id.factorial_button);

        // Set up the "Explicit Intent" button
        factorialButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get the input number from the text field
                int inputNumber = Integer.parseInt(inputField.getText().toString());

                // Create an Intent to start the FactorialActivity
                Intent explicitIntent = new Intent(MainActivity.this, MainActivity2.class);
                // Pass the input number as an extra
                explicitIntent.putExtra("input_number", inputNumber);

                // Start the FactorialActivity
                startActivity(explicitIntent);
            }
        });
    }


}
```
## MAINACTIVITY2.JAVA:
```
package com.example.explicitintent;


import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import java.math.BigInteger;
public class MainActivity2 extends AppCompatActivity{
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity2);

        // Get the input number from the Intent extra
        int inputNumber = getIntent().getIntExtra("input_number", 0);

        // Calculate the factorial of the input number using BigInteger
        BigInteger factorial = BigInteger.ONE;
        for (int i = 2; i <= inputNumber; i++) {
            factorial = factorial.multiply(BigInteger.valueOf(i));
        }
        // Display the factorial result in a TextView
        TextView resultTextView = findViewById(R.id.resultText);
        resultTextView.setText(
                "Factorial of " + inputNumber + " is: " + factorial
        );
    }
    public void back(View view) {
        Intent i = new Intent(getApplicationContext(), MainActivity.class);
        startActivity(i);
    }
}

```
## ACTIVITY MAIN.XML
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#EFF2F4"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/input_field"
        android:layout_width="252dp"
        android:layout_height="48dp"
        android:hint="Enter a number"
        android:inputType="number"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/factorial_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:backgroundTint="#D26BDA"
        android:text="FIND FACTORIAL"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/input_field" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="261dp"
        android:layout_height="99dp"
        android:text="FACTORIAL FINDER"
        android:textAlignment="center"
        android:textColor="#AE218F"
        android:textSize="34sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toTopOf="@+id/input_field"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.72" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## ACTIVITY2.XML :
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#EFF2F4"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/resultText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="The Factorial is : "
        android:textColor="#AE218F"
        android:textSize="34sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.349" />

    <Button
        android:id="@+id/button"
        android:layout_width="122dp"
        android:layout_height="65dp"
        android:backgroundTint="#C362CA"
        android:onClick="back"
        android:text="BACK"
        android:textColorLink="#C85A5A"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/resultText" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## OUTPUT

<img width="1907" height="1014" alt="image" src="https://github.com/user-attachments/assets/2ee415b4-d61f-496f-8e4b-ddf3466239db" />
<img width="1907" height="1011" alt="image" src="https://github.com/user-attachments/assets/f4e88010-091d-4efb-9392-18b45a3fa338" />


## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


