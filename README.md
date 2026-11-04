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
```
/*
Program to print the text “ExplicitIntent”.
Developed by: MAHALINGA JEYANTH V
Registeration Number : 212224220057
*/
```
ACTIVITY MAIN.JAVA1:
```

package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;
import java.math.BigInteger;

public class MainActivity extends AppCompatActivity {

    EditText numberInput;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        numberInput = findViewById(R.id.numberInput);
    }

    public void newsScreen(View view) {
        String input = numberInput.getText().toString().trim();

        if (input.isEmpty()) {
            Toast.makeText(this, "Enter a number",
                    Toast.LENGTH_SHORT).show();
            return;
        }

        try {
            int n = Integer.parseInt(input);

            if (n < 0 || n > 1000) {
                Toast.makeText(this, "Enter a number from 0 to 1000",
                        Toast.LENGTH_SHORT).show();
                return;
            }

            BigInteger fact = BigInteger.ONE;

            for (int i = 2; i <= n; i++) {
                fact = fact.multiply(BigInteger.valueOf(i));
            }

            Intent intent = new Intent(
                    MainActivity.this, MainActivity2.class);
            intent.putExtra("RESULT", fact.toString());
            startActivity(intent);

        } catch (NumberFormatException e) {
            Toast.makeText(this, "Invalid number",
                    Toast.LENGTH_SHORT).show();
        }
    }
}
```
ACTIVITY MAIN.JAVA2:
```
package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        TextView resultTextView =
                findViewById(R.id.resultTextView);

        String result = getIntent().getStringExtra("RESULT");
        resultTextView.setText(result);
    }

    public void homeScreen(View view) {
        Intent intent = new Intent(
                MainActivity2.this, MainActivity.class);
        startActivity(intent);
        finish();
    }
}
```
ACTIVITY MAIN.XML1:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/factorial_calculator"
        android:textSize="24sp"
        android:textStyle="bold" />

    <EditText
        android:id="@+id/numberInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:importantForAutofill="no"
        android:padding="16dp"
        android:hint="@string/enter_a_number"
        android:inputType="number"
        android:gravity="center" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/calculate_factorial"
        android:onClick="newsScreen" />

</LinearLayout>
```
ACTIVITY MAIN.XML2:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/the_factorial_result_is"
        android:textSize="22sp"
        android:textStyle="bold" />

    <TextView
        android:id="@+id/resultTextView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/_0"
        android:textSize="20sp"
        android:gravity="center"
        android:padding="16dp" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/calculate_another"
        android:onClick="homeScreen" />

</LinearLayout>
```
## OUTPUT
UI DESIGN PART 1:
<img width="1920" height="1200" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/92f046e8-df19-4cc2-9f52-266f4ec9e33c" />

UI DESIGN PART 2:
<img width="1920" height="1200" alt="Screenshot (47)" src="https://github.com/user-attachments/assets/c3e06f26-333e-4f8a-8da7-a48c13ac12c1" />

ACTIVITY MAIN.JAVA:
<img width="1920" height="1200" alt="Screenshot (48)" src="https://github.com/user-attachments/assets/5f1a7fc9-606a-4d1f-b417-dc71acb8a264" />

<img width="1920" height="1200" alt="Screenshot (49)" src="https://github.com/user-attachments/assets/f6adefdb-ea9e-4809-991a-dbd002f8b961" />
<img width="1920" height="1200" alt="Screenshot (50)" src="https://github.com/user-attachments/assets/98c1a901-bf1d-4f4a-bd49-bbb3dde77bac" />


## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


