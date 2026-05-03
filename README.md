# 911-emergency-system
Emergency 911 web interface for reporting and awareness system
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Emergency 911</title>

<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap" rel="stylesheet">

<style>
body {
margin:0;
font-family:'Cairo',sans-serif;
background:#f5f7fa;
color:#222;
}

/* HEADER */
header {
background:white;
padding:20px;
box-shadow:0 2px 10px rgba(0,0,0,0.05);
}

/* ALERT */
.alert {
background:#fff3cd;
padding:12px 20px;
font-size:14px;
border-bottom:1px solid #eee;
}

/* HOME */
.main {
padding:20px;
display:grid;
grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
gap:20px;
}

/* BIG INFO BOX (جديد بالهوم) */
.info-box {
grid-column:1/-1;
background:white;
padding:20px;
border-radius:15px;
box-shadow:0 5px 15px rgba(0,0,0,0.05);
}

.stats {
display:flex;
gap:10px;
flex-wrap:wrap;
margin-top:10px;
}

.stat {
flex:1;
min-width:120px;
background:#f1f5f9;
padding:10px;
border-radius:10px;
text-align:center;
}

/* CARD */
.card {
background:white;
padding:25px;
border-radius:15px;
cursor:pointer;
transition:.3s;
}
.card:hover {
transform:translateY(-5px);
box-shadow:0 10px 20px rgba(0,0,0,0.08);
}

/* SECTION */
.section {display:none;padding:20px;}
.content {
background:white;
padding:25px;
border-radius:15px;
line-height:1.9;
}

/* BUTTON */
button {
padding:12px;
border:none;
border-radius:10px;
cursor:pointer;
}
.btn {
width:100%;
margin-top:10px;
background:#c62828;
color:white;
}
.back {background:#eee;margin-bottom:15px;}
</style>
</head>

<body>

<header>
<h2>🚨 نظام الطوارئ 911</h2>
<p>منصة استجابة الطوارئ الذكية</p>
</header>

<div class="alert">
⚠️ استخدم الرقم فقط للحالات الطارئة الحقيقية لتجنب تأخير الاستجابة
</div>

<!-- HOME (مطوّر ومليان محتوى) -->
<div id="home" class="main">

<!-- صندوق معلومات رئيسي -->
<div class="info-box">
<h3>📊 مركز الطوارئ</h3>
<p>
هذا النظام مصمم لتقديم استجابة سريعة للحالات الحرجة مثل الحوادث، الحرائق، الحالات الطبية، والجرائم.
كل بلاغ يتم تحليله وتوجيهه للجهة المختصة خلال ثوانٍ.
</p>

<div class="stats">
<div class="stat">⏱ سرعة استجابة عالية</div>
<div class="stat">🚑 إسعاف مباشر</div>
<div class="stat">🚒 دفاع مدني</div>
<div class="stat">🚓 شرطة طوارئ</div>
</div>
</div>

<!-- أزرار -->
<div class="card" onclick="openPage('about')">📘 تعريف النظام</div>
<div class="card" onclick="openPage('methods')">📡 طرق الإبلاغ</div>
<div class="card" onclick="openPage('guide')">⚠️ الإرشادات</div>
<div class="card" onclick="openPage('importance')">⏱ الأهمية</div>
<div class="card" onclick="openPage('complaint')">📝 شكوى</div>

<div class="card" style="background:#ffecec">
🔥 تنبيه: البلاغات الكاذبة تعرضك للمساءلة القانونية
</div>

<div class="card">
📍 النظام يعمل على مدار 24 ساعة / 7 أيام في الأسبوع
</div>

</div>

<!-- ABOUT -->
<div id="about" class="section">
<button class="back" onclick="goHome()">⬅ رجوع</button>
<div class="content">
<h2>ما هو 911؟</h2>
<p>
رقم الطوارئ 911 هو نظام عالمي للاستجابة السريعة يهدف إلى إنقاذ الأرواح
وتقليل الخسائر من خلال ربط مباشر بين المواطن وغرف العمليات.
</p>
</div>
</div>

<!-- METHODS -->
<div id="methods" class="section">
<button class="back" onclick="goHome()">⬅ رجوع</button>
<div class="content">

<h2>طرق الإبلاغ</h2>

<select>
<option>🚑 طوارئ طبية</option>
<option>🚒 حريق</option>
<option>🚓 حادث أمني</option>
</select>

<button class="btn" onclick="call911()">📞 اتصال مباشر</button>
<button class="btn" onclick="getLocation()">📍 إرسال الموقع</button>
<button class="btn" onclick="toggleRec()">🎤 تسجيل صوت</button>
<audio id="audio" controls style="width:100%;margin-top:10px;"></audio>

</div>
</div>

<!-- GUIDE (موسع جداً) -->
<div id="guide" class="section">
<button class="back" onclick="goHome()">⬅ رجوع</button>

<div class="content">
<h2>إرشادات التعامل مع الطوارئ</h2>

<p>
التعامل الصحيح مع حالات الطوارئ لا يقل أهمية عن سرعة الاتصال، بل في كثير من الحالات
هو العامل الذي يحدد نجاح عملية الإنقاذ أو فشلها.
</p>

<h3>🧠 أولاً: الحالة النفسية</h3>
<p>
يجب الحفاظ على هدوء الأعصاب قدر الإمكان، لأن الذعر يؤدي إلى إعطاء معلومات غير دقيقة
مثل الموقع أو نوع الحادث، مما يبطئ عملية الاستجابة.
</p>

<h3>📍 ثانياً: تحديد الموقع</h3>
<p>
الموقع هو أهم معلومة في أي بلاغ. يجب تحديده بدقة باستخدام:
- اسم الشارع  
- أقرب معلم معروف  
- أو مشاركة الموقع الجغرافي مباشرة
</p>

<h3>🗣 ثالثاً: وصف الحالة</h3>
<p>
يجب وصف الحادث بشكل مختصر وواضح مثل:
- عدد المصابين  
- نوع الحادث  
- هل يوجد خطر مستمر (حريق / انفجار / إطلاق نار)
</p>

<h3>🚨 رابعاً: أثناء المكالمة</h3>
<p>
لا تقم بإنهاء المكالمة إلا بعد أن يطلب منك موظف الطوارئ ذلك، لأنهم قد يحتاجون
لمعلومات إضافية أثناء إرسال فرق الإنقاذ.
</p>

<h3>⚠️ خامساً: الاستخدام المسؤول</h3>
<p>
استخدام الرقم لأغراض غير حقيقية يعتبر إساءة استخدام للنظام ويؤثر على حياة الآخرين
الذين يحتاجون الخدمة فعلياً.
</p>

</div>
</div>

<!-- IMPORTANCE -->
<div id="importance" class="section">
<button class="back" onclick="goHome()">⬅ رجوع</button>
<div class="content">
<h2>أهمية التبليغ السريع</h2>
<p>
كل ثانية تأخير قد تعني فقدان حياة أو تفاقم كارثة. التبليغ السريع يساعد في:
</p>
<ul>
<li>إنقاذ الأرواح</li>
<li>تقليل الخسائر</li>
<li>تحسين سرعة الاستجابة</li>
</ul>
</div>
</div>

<!-- COMPLAINT -->
<div id="complaint" class="section">
<button class="back" onclick="goHome()">⬅ رجوع</button>
<div class="content">

<h2>الشكاوى</h2>

<p>
يمكنك إرسال ملاحظاتك لتحسين جودة النظام.
</p>

<input placeholder="الاسم">
<input placeholder="البريد">
<textarea rows="5" placeholder="اكتب التفاصيل"></textarea>

<button class="btn">إرسال</button>

</div>
</div>

<script>
function openPage(id){
document.getElementById("home").style.display="none";
document.querySelectorAll(".section").forEach(s=>s.style.display="none");
document.getElementById(id).style.display="block";
}
function goHome(){
document.getElementById("home").style.display="grid";
document.querySelectorAll(".section").forEach(s=>s.style.display="none");
}

function call911(){
window.location.href="tel:911";
}

function getLocation(){
navigator.geolocation.getCurrentPosition(pos=>{
alert(pos.coords.latitude + "," + pos.coords.longitude);
});
}

let rec,chunks=[];
async function toggleRec(){
let stream=await navigator.mediaDevices.getUserMedia({audio:true});
rec=new MediaRecorder(stream);
chunks=[];
rec.ondataavailable=e=>chunks.push(e.data);
rec.onstop=()=>{
let blob=new Blob(chunks);
document.getElementById("audio").src=URL.createObjectURL(blob);
};
rec.start();
setTimeout(()=>rec.stop(),4000);
}
</script>

</body>
</html>
