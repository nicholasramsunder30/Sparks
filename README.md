ackage com.example.socialspark

import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        
        val mainView = findViewById<androidx.constraintlayout.widget.ConstraintLayout>(R.id.main)
        ViewCompat.setOnApplyWindowInsetsListener(mainView) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
        }

        val timeInput = findViewById<EditText>(R.id.timeInput) // Get input field where user types Morning/Midday/Afternoon
        val suggestButton = findViewById<Button>(R.id.suggestButton) // Get the suggest button
        val resultText = findViewById<TextView>(R.id.resultText) // Get text view where results will be displayed
        val resetButton = findViewById<Button>(R.id.resetButton) // Get reset button

        suggestButton.setOnClickListener { // When suggest button is clicked
            val input = timeInput.text.toString().trim() // Get user input and remove extra spaces

            if (input.equals("Morning", ignoreCase = true)) {
                resultText.text = "Morning: Start your day with a walk or check your socials ☀️" // Check if user entered "Morning"
            } else if (input.equals("Midday", ignoreCase = true)) {
                resultText.text = "Midday: Chat with friends or grab lunch 🍔" // Check if user entered "Midday"
            } else if (input.equals("Afternoon", ignoreCase = true)) {
                resultText.text = "Afternoon: Relax, watch content or connect online 🎬" // Check if user entered "Afternoon"
            } else {
                resultText.text = "Error: Please enter Morning, Midday or Afternoon"// If input is incorrec
            }
        }

        resetButton.setOnClickListener {// When reset button is clicked
            timeInput.text.clear() 
            resultText.text = ""  // Clear input field
        }
    }
}

REPORT
Social Spark is a simple Android application developed using Kotlin in Android Studio. The purpose of the app is to help users maintain social interaction by suggesting activities based on the time of day entered by the user.The app was created to assist users in staying socially active during busy days. It allows users to input a time of day such as “Morning”, “Midday”, or “Afternoon” and receive a relevant social suggestion.
FEATURES
A text input field where the user enters the time of day
A “Suggest” button that generates a social activity
A result display area showing the suggestion
A “Reset” button to clear input and output
Error handling for incorrect input

The user types a time of day into the input field and presses the “Suggest” button. The app uses if statements to check the input:

If the input is “Morning”, a morning activity is displayed
If the input is “Midday”, a midday activity is displayed
If the input is “Afternoon”, an afternoon activity is displayed
If the input is incorrect, an error message is shown

The Social Spark app successfully meets the requirements by providing an interactive and user-friendly way to suggest social activities. It demonstrates the use of user input, conditional logic, and error handling in Android development.
