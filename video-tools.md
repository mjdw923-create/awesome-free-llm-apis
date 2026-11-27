# الأدوات المجانية الخاصة بالفيديو في هذا المستودع

> مستخرجة من `data.json` (آخر تحديث للبيانات: 2026-11-15) ومن `sources.json`.
>
> **تنبيه مهم:** كل النماذج التالية **تفهم الفيديو كمُدخل** (تحليل، تلخيص، وصف، أسئلة وأجوبة عن محتوى الفيديو)، ومخرجاتها **نص فقط**.
> المستودع **لا يحتوي على أي أداة مجانية لتوليد الفيديو** (Text-to-Video مثل CogVideoX أو Veo أو Sora).

## 1. Google Gemini 🇺🇸 — مزوّد مباشر

- **الحصول على المفتاح:** https://aistudio.google.com/app/apikey
- **Base URL:** `https://generativelanguage.googleapis.com/v1beta`
- **الشروط:** طبقة مجانية بدون بطاقة ائتمان، وقد تستخدم Google الطلبات المجانية لتحسين منتجاتها.

| النموذج | السياق | أقصى مخرجات | المُدخلات |
| --- | --- | --- | --- |
| `gemini-3.8-flash` | 1M | 65K | نص + صورة + صوت + فيديو |
| `gemini-3.6-flash` | 1M | 65K | نص + صورة + صوت + فيديو |
| `gemini-3.5-flash-lite` | 1M | 65K | نص + صورة + صوت + فيديو |
| `gemini-3.1-flash-lite` | 1M | 65K | نص + صورة + صوت + فيديو |
| `gemini-2.5-flash` | 1M | 65K | نص + صورة + صوت + فيديو |
| `gemini-2.5-flash-lite` | 1M | 65K | نص + صورة + صوت + فيديو |

## 2. Z AI (Zhipu AI) 🇨🇳 — مزوّد مباشر

- **الحصول على المفتاح:** https://open.bigmodel.cn/usercenter/apikeys
- **Base URL:** `https://open.bigmodel.cn/api/paas/v4`
- **الشروط:** نماذج مجانية دائمة بدون بطاقة ائتمان.

| النموذج | السياق | أقصى مخرجات | المُدخلات | الحد |
| --- | --- | --- | --- | --- |
| `glm-4.6v-flash` | 128K | 32K | فيديو / صورة / نص / ملف | طلب متزامن واحد |

## 3. OpenRouter 🇺🇸 — منصة استدلال

- **الحصول على المفتاح:** https://openrouter.ai/keys
- **Base URL:** `https://openrouter.ai/api/v1`
- **الحدود:** 20 طلب/دقيقة و50 طلب/يوم لكل النماذج المجانية مجتمعة، وترتفع إلى 1000 طلب/يوم لمن اشترى رصيداً بقيمة 10 على الأقل.

| النموذج | السياق | أقصى مخرجات | المُدخلات |
| --- | --- | --- | --- |
| `google/gemma-4-26b-a4b-it:free` | 262K | 32K | نص + صورة + فيديو |
| `google/gemma-4-31b-it:free` | 262K | 32K | نص + صورة + فيديو |
| `nvidia/nemotron-3.5-super-vl:free` | 1M | 131K | نص + صورة + فيديو |
| `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning:free` | 256K | 65K | نص + صورة + صوت + فيديو |

## 4. Kilo Code 🇺🇸 — منصة استدلال (بدون مفتاح API)

- **الحساب:** https://app.kilo.ai/profile
- **Base URL:** `https://api.kilo.ai/api/gateway`
- **الحدود والشروط:** 200 طلب/ساعة لكل عنوان IP. نقاط NVIDIA المجانية مخصّصة للتجربة فقط، وتُسجَّل الطلبات، فلا ترسل عبرها بيانات شخصية أو سرية.

| النموذج | السياق | أقصى مخرجات | المُدخلات |
| --- | --- | --- | --- |
| `nvidia/nemotron-3.5-super-vl:free` | 1M | 131K | متعدد الوسائط (يدعم الفيديو على OpenRouter) |
| `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning:free` | 256K | 65K | متعدد الوسائط (يدعم الفيديو على OpenRouter) |

## 5. NVIDIA NIM 🇺🇸 — منصة استدلال

- **الرابط:** https://build.nvidia.com/explore/discover
- **Base URL:** `https://integrate.api.nvidia.com/v1`
- **الشروط:** مجاني لأعضاء NVIDIA Developer Program، والحدود تختلف من نموذج لآخر. مخصّص للنماذج الأولية والتجارب، والاستخدام الإنتاجي يحتاج ترخيص NVIDIA AI Enterprise.
- يذكر المستودع "+92 نموذجاً آخر" تشمل فئات نص وصورة و**فيديو** وكلام وتضمينات (Embeddings)، لكنه **لا يسمّي نماذج الفيديو تحديداً**. راجع الكتالوج على الرابط أعلاه.

## ما تم استبعاده

- `@cf/meta/llama-4-scout-17b-16e-instruct` على Cloudflare Workers AI: مصنّف "Multimodal" في البيانات، لكن المصدر يذكر فهم **النص والصورة** فقط، دون الفيديو.

## طريقة الاستخدام

> لم تُجرَّب الأمثلة التالية من بيئة العمل لأن الاتصال بهذه الخوادم محجوب فيها. شغّلها في Google Colab أو على جهازك.
> كل النماذج تُرجع **نصاً**: تلخيص، وصف، تفريغ للكلام، توقيتات، أسئلة وأجوبة.

### الطريقة الأسهل بدون كود: Google AI Studio

1. افتح https://aistudio.google.com وسجّل الدخول بحساب Google.
2. اختر نموذجاً مثل Gemini 3.8 Flash، ثم ارفع الفيديو بزر ➕ أو الصق رابط يوتيوب.
3. اكتب طلبك، مثلاً: "لخّص هذا الفيديو بالعربية مع التوقيتات".

### 1) Gemini في Colab (يستخدم السر `GEMINI_KEY` الموجود في دفترك)

```python
!pip install -q google-genai
import time
from google import genai
from google.colab import userdata, files

client = genai.Client(api_key=userdata.get("GEMINI_KEY"))

path = next(iter(files.upload()))          # اختر ملف الفيديو من جهازك
video = client.files.upload(file=path)
while video.state.name == "PROCESSING":     # انتظر انتهاء المعالجة
    time.sleep(5)
    video = client.files.get(name=video.name)

r = client.models.generate_content(
    model="gemini-3.8-flash",
    contents=[video, "لخّص هذا الفيديو بالعربية واذكر أهم اللحظات مع توقيتها"],
)
print(r.text)
```

**فيديو من يوتيوب مباشرة، بدون رفع:**

```python
from google.genai import types
r = client.models.generate_content(
    model="gemini-3.8-flash",
    contents=types.Content(parts=[
        types.Part(file_data=types.FileData(file_uri="https://www.youtube.com/watch?v=VIDEO_ID")),
        types.Part(text="ما الفكرة الرئيسية لهذا الفيديو؟"),
    ]),
)
print(r.text)
```

**فيديو من Google Drive:** شغّل `from google.colab import drive; drive.mount('/content/drive')`،
ثم استخدم `path = "/content/drive/MyDrive/اسم_الفيديو.mp4"` بدلاً من `files.upload()`.

### 2) OpenRouter (Gemma 4 / Nemotron)

```python
import base64, requests
KEY = "sk-or-..."   # من https://openrouter.ai/keys
b64 = base64.b64encode(open("video.mp4", "rb").read()).decode()

r = requests.post(
    "https://openrouter.ai/api/v1/chat/completions",
    headers={"Authorization": f"Bearer {KEY}"},
    json={
        "model": "google/gemma-4-31b-it:free",
        "messages": [{"role": "user", "content": [
            {"type": "text", "text": "صف ما يحدث في هذا الفيديو"},
            {"type": "video_url", "video_url": {"url": f"data:video/mp4;base64,{b64}"}},
        ]}],
    },
    timeout=300,
)
print(r.json()["choices"][0]["message"]["content"] if r.ok else r.text)
```

استخدم مقاطع قصيرة وصغيرة الحجم، لأن ترميز base64 يكبّر حجم الطلب.

### 3) Z AI: `glm-4.6v-flash`

```python
import requests
KEY = "..."   # من https://open.bigmodel.cn/usercenter/apikeys
r = requests.post(
    "https://open.bigmodel.cn/api/paas/v4/chat/completions",
    headers={"Authorization": f"Bearer {KEY}"},
    json={
        "model": "glm-4.6v-flash",
        "messages": [{"role": "user", "content": [
            {"type": "video_url", "video_url": {"url": "https://example.com/video.mp4"}},
            {"type": "text", "text": "لخّص هذا الفيديو"},
        ]}],
    },
    timeout=300,
)
print(r.json()["choices"][0]["message"]["content"] if r.ok else r.text)
```

يجب أن يكون رابط الفيديو عاماً ومباشراً. الحد طلب متزامن واحد، فلا ترسل طلبات متوازية.

### 4) Kilo Code (بدون مفتاح)

نفس كود OpenRouter مع تغييرين:
- العنوان: `https://api.kilo.ai/api/gateway/chat/completions`
- النموذج: `nvidia/nemotron-3.5-super-vl:free`، مع حذف ترويسة `Authorization`.

دعم الفيديو على Kilo غير موثّق صراحة في المستودع، وهو مصنّف فيه "متعدد الوسائط" فقط. لا ترسل بيانات خاصة لأن الطلبات تُسجَّل.

### أي أداة تختار؟

| الحاجة | الأنسب |
| --- | --- |
| فيديو طويل أو يوتيوب أو فهم الصوت والكلام | **Gemini** (سياق 1M ويدعم الصوت) |
| بدون حساب ولا مفتاح | **Kilo Code** |
| بديل احتياطي عند نفاد حصة Gemini | **OpenRouter** أو **GLM-4.6V-Flash** |
| **توليد** فيديو من نص | غير متوفر في هذا المستودع |
