# xmljson
MAD LAB
<br>
###Closed Project<BR>
TTS<br>
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
'''
xmljson<br>
activity_main.xml<br>

    <?xml version="1.0" encoding="utf-8"?>
    <androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <com.google.android.material.button.MaterialButton
    android:id="@+id/parse_xml"
    android:layout_width="wrap_content"
    android:layout_height="54dp"
    android:layout_marginBottom="8dp"
    android:text="Parse XML Data"
    app:layout_constraintBottom_toTopOf="@+id/parse_json"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintVertical_bias="0.24000001"
    app:layout_constraintVertical_chainStyle="packed" />
    <com.google.android.material.button.MaterialButton
    android:id="@+id/parse_json"
    android:layout_width="wrap_content"
    android:layout_height="54dp"
    android:layout_marginBottom="8dp"
    android:text="Parse JSON Data"
    app:layout_constraintBottom_toTopOf="@+id/data_type"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/parse_xml" />
    <com.google.android.material.textview.MaterialTextView
    android:id="@+id/data_type"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="24dp"
    android:layout_marginBottom="16dp"
    android:text=""
    android:textSize="24sp"
    app:layout_constraintBottom_toTopOf="@+id/city_name"
    <?xml version="1.0" encoding="utf-8"?>
    <data>
    <City_Name>Mysore</City_Name>
    <Latitude>22.295</Latitude>
    <Longitude>76.639</Longitude>
    <Temperature>42</Temperature>
    <Humidity>80%</Humidity>
    </data>
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/parse_json" />
    <com.google.android.material.textview.MaterialTextView
    android:id="@+id/city_name"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="8dp"
    android:layout_marginBottom="8dp"
    android:text="City Name :"
    android:textSize="24sp"
    app:layout_constraintBottom_toTopOf="@+id/latitude"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/data_type" />
    <com.google.android.material.textview.MaterialTextView
    android:id="@+id/latitude"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="8dp"
    android:layout_marginBottom="8dp"
    android:text="Latitude :"
    android:textSize="24sp"
    app:layout_constraintBottom_toTopOf="@+id/longitude"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/city_name" />
    <com.google.android.material.textview.MaterialTextView
    android:id="@+id/longitude"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="8dp"
    android:layout_marginBottom="8dp"
    android:text="Longitude :"
    android:textSize="24sp"
    app:layout_constraintBottom_toTopOf="@+id/temprature"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/latitude" />
    <com.google.android.material.textview.MaterialTextView
    android:id="@+id/temprature"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="8dp"
    android:layout_marginBottom="8dp"
    android:text="Temprature :"
    android:textSize="24sp"
    app:layout_constraintBottom_toTopOf="@+id/humidity"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/longitude" />
    <com.google.android.material.textview.MaterialTextView
    android:id="@+id/humidity"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="8dp"
    android:layout_marginBottom="8dp"
    android:text="Humidity :"
    android:textSize="24sp"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/temprature" />
    </androidx.constraintlayout.widget.ConstraintLayout>

kotlin<br>

    import android.annotation.SuppressLint
    import androidx.appcompat.app.AppCompatActivity
    import android.os.Bundle
    import android.widget.Button
    import android.widget.TextView
    import org.json.JSONObject
    import java.io.IOException
    import java.nio.charset.Charset
    import javax.xml.parsers.DocumentBuilderFactory
    class MainActivity : AppCompatActivity() {
    private lateinit var parseXMLBtn: Button
    private lateinit var parseJSONBtn: Button
    private lateinit var datatype : TextView
    private lateinit var cityName: TextView
    private lateinit var latitude: TextView
    private lateinit var longitude: TextView
    private lateinit var temprature: TextView
    private lateinit var humidity: TextView
    override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)
    parseXMLBtn = findViewById(R.id.parse_xml)
    parseXMLBtn.setOnClickListener { parseXML() }
    parseJSONBtn = findViewById(R.id.parse_json)
    parseJSONBtn.setOnClickListener { parseJSON() }
    parseXMLBtn.setOnClickListener { parseXML() }
    datatype = findViewById(R.id.data_type)
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/longitude" />
    <com.google.android.material.textview.MaterialTextView
    android:id="@+id/humidity"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="8dp"
    android:layout_marginBottom="8dp"
    android:text="Humidity :"
    android:textSize="24sp"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.5"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/temprature" />
    </androidx.constraintlayout.widget.ConstraintLayout>
    cityName = findViewById(R.id.city_name)
    latitude = findViewById(R.id.latitude)
    longitude = findViewById(R.id.longitude)
    temprature = findViewById(R.id.temprature)
    humidity = findViewById(R.id.humidity)
    }
    @SuppressLint("SetTextI18n")
    fun parseXML(){
    datatype.text = "XML Data"
    try {
    val iStream = assets.open("myxml.xml")
    val builderFactory = DocumentBuilderFactory.newInstance()
    var docBuilder = builderFactory.newDocumentBuilder()
    var doc = docBuilder.parse(iStream)
    cityName.text = "City Name : " +
    doc.getElementsByTagName("City_Name").item(0).getFirstChild().getNodeValue()
    latitude.text = "Latitude : " +
    doc.getElementsByTagName("Latitude").item(0).getFirstChild().getNodeValue()
    longitude.text = "Longitude : " +
    doc.getElementsByTagName("Longitude").item(0).getFirstChild().getNodeValue()
    temprature.text = "Temperature : " +
    doc.getElementsByTagName("Temperature").item(0).getFirstChild().getNodeValue()
    humidity.text = "Humidity : " +
    doc.getElementsByTagName("Humidity").item(0).getFirstChild().getNodeValue()
    }
    catch (ex: IOException) {
    }
    }
    @SuppressLint("SetTextI18n")
    fun parseJSON(){
    datatype.text = "JSON Data"
    val obj = JSONObject(loadJSONFromAsset())
    cityName.text = "City Name : " + obj.getString("City Name")
    latitude.text = "Latitude : " + obj.getString("Latitude")
    longitude.text = "Longitude : " + obj.getString("Longitude")
    temprature.text = "Temperature : " + obj.getString("Temperature")
    humidity.text = "Humidity : " + obj.getString("Humidity")
    }
    private fun loadJSONFromAsset(): String {
    val json: String?
    try {
    val inputStream = assets.open("myjson.json")
    val size = inputStream.available()
    val buffer = ByteArray(size)
    val charset: Charset = Charsets.UTF_8
    inputStream.read(buffer)
    inputStream.close()
    json = String(buffer, charset)
    }
    catch (ex: IOException) {
    ex.printStackTrace()
    return ""
    }
    return json
    }
    }
