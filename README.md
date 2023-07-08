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

<br>phone dialler<br>
permissions in android manifest.xml<br>

    <uses-permission android:name="android.permission.CALL_PHONE" />
    <uses-permission android:name="android.permission.MANAGE_OWN_CALLS" />
    <uses-permission android:name="android.permission.MANAGE_OUTGOING_CALLS">
        <uses-permission android:name="android.permission.WRITE_CONTACTS" />
        <uses-permission android:name="android.permission.READ_CONTACTS" />

<br>

        Activity_main.xml
        <?xml version="1.0" encoding="utf-8"?>
        <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android" 
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools" 
        android:layout_width="match_parent" 
        android:layout_height="match_parent" 
        tools:context=".MainActivity">
        <LinearLayout android:layout_width="wrap_content" 
        android:layout_height="wrap_content"
            android:orientation="vertical" 
            app:layout_constraintBottom_toBottomOf="parent" 
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.5"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent">
                <LinearLayout android:layout_width="wrap_content"
                android:layout_height="wrap_content" 
                android:orientation="horizontal">
                <com.google.android.material.textview.MaterialTextView 
                android:id="@+id/contact"
                android:layout_width="200dp"
                    android:layout_height="100dp" 
                    android:gravity="center" 
                    android:textSize="24sp"/>
                    <com.google.android.material.textview.MaterialTextView 
                    android:id="@+id/clear" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center"
        android:text="X" android:textSize="24sp" /> </LinearLayout> <LinearLayout android:layout_width="wrap_content" android:layout_height="wrap_content" android:orientation="horizontal"> <com.google.android.material.textview.MaterialTextView android:id="@+id/one" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="1" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/two" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="2" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/three" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="3" android:textSize="24sp" /> </LinearLayout> <LinearLayout android:layout_width="wrap_content" android:layout_height="wrap_content" android:orientation="horizontal">
        <com.google.android.material.textview.MaterialTextView android:id="@+id/four" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="4" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/five" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="5" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/six" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="6" android:textSize="24sp" /> </LinearLayout> <LinearLayout android:layout_width="wrap_content" android:layout_height="wrap_content" android:orientation="horizontal"> <com.google.android.material.textview.MaterialTextView android:id="@+id/seven" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="7" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/eight"
        android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="8" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/nine" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="9" android:textSize="24sp" /> </LinearLayout> <LinearLayout android:layout_width="wrap_content" android:layout_height="wrap_content" android:orientation="horizontal"> <com.google.android.material.textview.MaterialTextView android:id="@+id/star" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="*" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/zero" android:layout_width="100dp" android:layout_height="100dp" android:gravity="center" android:text="0" android:textSize="24sp" /> <com.google.android.material.textview.MaterialTextView android:id="@+id/hash" android:layout_width="100dp" android:layout_height="100dp"
        android:gravity="center" android:text="#" android:textSize="24sp" /> </LinearLayout> <LinearLayout android:layout_width="wrap_content" android:layout_height="wrap_content" android:orientation="horizontal"> <com.google.android.material.button.MaterialButton android:id="@+id/call" android:layout_width="134dp" android:layout_height="54dp" android:layout_margin="8dp" android:text="Call"/> <com.google.android.material.button.MaterialButton android:id="@+id/save" android:layout_width="134dp" android:layout_height="54dp" android:layout_margin="8dp" android:text="Save"/> </LinearLayout> </LinearLayout> </androidx.constraintlayout.widget.ConstraintLayout>

        <br>
kotlin<br>

    import android.R.attr.phoneNumber
    import android.content.Intent 
    import android.net.Uri 
    import android.os.Bundle
    import android.provider.ContactsContract 
    import android.widget.Button
    import android.widget.TextView
    import androidx.appcompat.app.AppCompatActivity class MainActivity :AppCompatActivity() {
        private lateinit var saveBtn: Button
        private lateinit var callBtn: Button 
        private lateinit var zero: TextView 
        private lateinit var one: TextView
        private lateinit var two: TextView 
        private lateinit var three: TextView
            private lateinit var four: TextView
            private lateinit var five: TextView
            private lateinit var six: TextView
            private lateinit var seven: TextView
                private lateinit var eight: TextView
                private lateinit var nine: TextView 
                private lateinit var star: TextView 
                private lateinit var hash: TextView
                private lateinit var clear: TextView
                private lateinit var contact: TextView 
                override fun onCreate(savedInstanceState: Bundle?) {
                    super.onCreate(savedInstanceState)
                    setContentView(R.layout.activity_main)
                    saveBtn = findViewById(R.id.save) 
                    callBtn = findViewById(R.id.call)
                        zero = findViewById(R.id.zero)
                        one = findViewById(R.id.one) 
                        two = findViewById(R.id.two)
                        three = findViewById(R.id.three) 
                        four = findViewById(R.id.four)
                        five = findViewById(R.id.five)
                            six = findViewById(R.id.six) 
                            seven = findViewById(R.id.seven)
                            eight = findViewById(R.id.eight)
                            nine = findViewById(R.id.nine)
                            star = findViewById(R.id.star)
    hash = findViewById(R.id.hash)
    clear = findViewById(R.id.clear)
    contact = findViewById(R.id.contact)
    zero.setOnClickListener { pressButton("0", true) }
        one.setOnClickListener { pressButton("1", true) }
        two.setOnClickListener { pressButton("2", true) }
        three.setOnClickListener { pressButton("3", true) }
        four.setOnClickListener { pressButton("4", true) }
            five.setOnClickListener { pressButton("5", true) } 
            six.setOnClickListener { pressButton("6", true) } 
            seven.setOnClickListener { pressButton("7", true) }
            eight.setOnClickListener { pressButton("8", true)}
            nine.setOnClickListener { pressButton("9", true) }
    star.setOnClickListener { pressButton("*", true) }
    hash.setOnClickListener { pressButton("#", true) }
    clear.setOnClickListener { contact.text = "" } 
    callBtn.setOnClickListener
        {
            val intent = Intent(Intent.ACTION_CALL, Uri.parse("tel:" + "${contact.text}"))
            startActivity(intent) 
            } 
        saveBtn.setOnClickListener {
            val intent = Intent( ContactsContract.Intents.SHOW_OR_CREATE_CONTACT, Uri.parse("tel:" + contact.text)) intent.putExtra(ContactsContract.Intents.EXTRA_FORCE_CREATE, true)
            startActivity(intent) } 
            }
            fun pressButton(string: String, clear: Boolean) {
                if (!clear) {
                contact.text = ""
    }
    else { contact.append(string) } 
    }
    }
