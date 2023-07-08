# xmljson
MAD LAB
<br>
###Closed Project
TTS
activity_main.xml
_________________
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">
<EditText
android:id="@+id/editText"
android:layout_width="312dp"
android:layout_height="146dp"
android:ems="10"
android:inputType="textPersonName"
android:text=" text"
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintHorizontal_bias="0.646"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toTopOf="parent"
app:layout_constraintVertical_bias="0.305" />
<Button
android:id="@+id/textToSpeechButton"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text=" textToSpeechButton"
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintHorizontal_bias="0.498"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toTopOf="parent"
app:layout_constraintVertical_bias="0.576" />
</androidx.constraintlayout.widget.ConstraintLayout>

kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.speech.tts.TextToSpeech
import android.util.Log
import android.widget.EditText
import com.google.android.material.button.MaterialButton
import java.util.*
class MainActivity : AppCompatActivity(), TextToSpeech.OnInitListener{
private var textToSpeech: TextToSpeech? = null
private lateinit var textToSpeechButton : MaterialButton
private lateinit var textInput : EditText
override fun onCreate(savedInstanceState: Bundle?) {
super.onCreate(savedInstanceState)
setContentView(R.layout.activity_main)
textToSpeechButton = findViewById(R.id.textToSpeechButton)
textInput = findViewById(R.id.editText)
textToSpeechButton!!.isEnabled= false
textToSpeech = TextToSpeech(this,this)
textToSpeechButton!!.setOnClickListener{convertToSpeech()}
}
override fun onInit(status: Int) {
if(status == TextToSpeech.SUCCESS){
val result = textToSpeech!!.setLanguage(Locale.US)
if(result == TextToSpeech.LANG_MISSING_DATA || result ==
TextToSpeech.LANG_NOT_SUPPORTED){
Log.e("TTS","Language specified NOT SUPPORTED")
}
else{
textToSpeechButton!!.isEnabled = true
}
}
else{
}
}
Log.e("TTS","Initialization Failed")
private fun convertToSpeech(){
val text = textInput!!.text.toString()
textToSpeech!!.speak(text, TextToSpeech.QUEUE_FLUSH, null, "")
}
public override fun onDestroy()
{
if (textToSpeech != null)
{
textToSpeech!!.stop()
textToSpeech!!.shutdown()
super.onDestroy()
}}}
