/ Create first input field
TextField billAmountField = new TextField(
  labelText: “Bill amount(\$)”,
  keyboardType: TextInputType.number,
  onChanged: (InputValue value) {
    try {
      billAmount = double.parse(value.text);
    } catch (exception) {
      billAmount = 0.0;
    }
  }
);
 
// Create another input field
TextField tipPercentageField = new TextField(
  labelText: “Tip %”,
  keyboardType: TextInputType.number,
  hintText: “15”,
  onChanged: (InputValue value) {
    try {
      tipPercentage = double.parse(value.text);
    } catch (exception) {
      tipPercentage = 0.0;
    }
  }
);
// Create button
RaisedButton calculateButton = new RaisedButton(
    child: new Text(“Calculate”),
    onPressed: () {
        // More code goes here
    }
);
// Calculate tip and total
double calculatedTip = billAmount * tipPercentage / 100.0;
double total = billAmount + calculatedTip;
 
// Generate dialog
AlertDialog dialog = new AlertDialog(
content: new Text(“Tip: \$$calculatedTip \n”
    “Total: \$$total”)
);
 
// Show dialog
showDialog(context: context, child: dialog);
Container container = new Container(
  padding: const EdgeInsets.all(16.0),
  child: new Column(
    children: [ billAmountField,
                tipPercentageField,
                calculateButton ]
  )
);
void main() {
  runApp(new MaterialApp(
    title: ‘Tip Calculator’,
    home: new TipCalculator()
  ));
}
<?xml version="1.0" encoding="utf-8"?> 
<RelativeLayout
	xmlns:android="http://schemas.android.com/apk/res/android"
	xmlns:tools="http://schemas.android.com/tools"
	android:id="@+id/idRLContainer"
	android:layout_width="match_parent"
	android:layout_height="match_parent"
	android:background="@color/purple_200"
	android:orientation="vertical"
	tools:context=".MainActivity"> 

	<!--on below line we are adding an image view-->
	<ImageView
		android:id="@+id/idIVLogo"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:layout_centerInParent="true"
		android:layout_margin="25dp"
		android:src="@drawable/gfglogo"
		android:tint="@color/white" /> 

	<!--on below line we are creating progress bar-->
	<ProgressBar
		android:id="@+id/idPBLoading"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:layout_below="@id/idIVLogo"
		android:layout_centerInParent="true"
		android:indeterminateTint="@color/white" /> 

</RelativeLayout>
package com.gtappdevelopers.kotlingfgproject 

import android.content.Intent 
import android.os.Bundle 
import android.os.Handler 
import android.view.WindowManager 
import androidx.appcompat.app.AppCompatActivity 

class MainActivity : AppCompatActivity() { 

	override fun onCreate(savedInstanceState: Bundle?) { 
		super.onCreate(savedInstanceState) 

		// on below line we are configuring 
		// our window to full screen 
		window.setFlags( 
			WindowManager.LayoutParams.FLAG_FULLSCREEN, 
			WindowManager.LayoutParams.FLAG_FULLSCREEN 
		) 
		setContentView(R.layout.activity_main) 
		
		// on below line we are calling 
		// handler to run a task 
		// for specific time interval 
		Handler().postDelayed({ 
			// on below line we are 
			// creating a new intent 
			val i = Intent( 
				this@MainActivity, 
				MainActivity2::class.java 
			) 
			// on below line we are 
			// starting a new activity. 
			startActivity(i) 
			
			// on the below line we are finishing 
			// our current activity. 
			finish() 
		}, 2000) 
	} 
}
<?xml version="1.0" encoding="utf-8"?> 
<RelativeLayout
	xmlns:android="http://schemas.android.com/apk/res/android"
	xmlns:tools="http://schemas.android.com/tools"
	android:layout_width="match_parent"
	android:layout_height="match_parent"
	tools:context=".MainActivity2"> 

	<!--on below line we are creating 
		a text for our app-->
	<TextView
		android:id="@+id/idTVHeading"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:layout_centerInParent="true"
		android:layout_margin="20dp"
		android:gravity="center"
		android:padding="10dp"
		android:text="Welcome to Geeks for Geeks"
		android:textAlignment="center"
		android:textColor="@color/black"
		android:textSize="20sp"
		android:textStyle="bold" /> 

</RelativeLayout>
<!--on below line we are adding a style for MainActivity-->
<activity
	android:name=".MainActivity"
	android:theme="@style/Theme.MaterialComponents.DayNight.NoActionBar"> 
			<intent-filter> 
				<action android:name="android.intent.action.MAIN" /> 

				<category android:name="android.intent.category.LAUNCHER" /> 
			</intent-filter> 
</activity>
