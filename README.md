# Agno Tabanlı Akıllı İK Asistanı (NLQ to SQL & Semantic Search)

Bu proje, doğal dildeki aday arama sorgularını (NLQ) analiz ederek **SQL filtreleme** ve **Semantik Arama** tekniklerini birleştiren, Agno framework tabanlı hibrit bir İK asistanı sistemidir.

## 🚀 Temel Özellikler

* **Hibrit Arama Mimarisi:** Yapılandırılmış veriler (yaş, okul) için SQL; soyut yetenekler (iletişim becerisi, liderlik) için semantik arama.


* **Gelişmiş Mantık Yürütme (Reasoning):** `reasoning=True` bayrağı ile sorguların neden ve nasıl ayrıştırıldığını gösteren şeffaf Chain-of-Thought (CoT) süreci.


* **Dinamik Bellek Yönetimi:** Oturum bazlı kısa süreli hafıza ve Mem0 entegrasyonu ile uzun vadeli kullanıcı tercihlerini hatırlama.


* **Reranker Optimizasyonu:** Embedding sonuçlarını CrossEncoder (Cohere veya Sentence Transformers) kullanarak yeniden sıralayan yüksek isabetli sonuç katmanı.



## 🏗️ Mimari Yapı

Sistem Agno framework'ünün 4 temel katmanı üzerine kurulmuştur:

1. **Flags:** Modelin zekasına güvenilen en alt seviye yapılandırmalar (örn: `reasoning=True`).


2. **Tools:** SQLTools, WebTools ve DockerTools gibi dış sistemlerle etkileşimi sağlayan yetenekler.


3. **Agents:** Karar mekanizması; Router Agent, SQL Parser Agent ve Semantic Agent.


4. **Workflows:** Çok adımlı süreçlerin (Sorgu Parse -> DB Arama -> Rerank -> Özetleme) yönetimi.



## 🧠 Bellek Türleri ve Kullanımı

| Tür | Açıklama | Teknoloji |
| --- | --- | --- |
| **Kısa Süreli** | Mevcut oturumdaki konuşma geçmişi ve state yönetimi.

 | SQLite / RAM || **Uzun Süreli** | Kullanıcı tercihleri (örn: "Hep kıdemli adaylar getir").

 | Mem0 / User Memory || **Özetleme** | Uzun sohbetlerin bağlamı korunarak sıkıştırılması.

 | Session Summary |

## 📊 Performans ve Doğruluk Değerlendirmesi

* **Reasoning Etkisi:** SQL Agent doğruluğu mantık yürütme ile %40'tan %80'e çıkmaktadır.


* **Router Başarısı:** Sorguları doğru ajana yönlendirme skoru 10 üzerinden 8.6 olarak ölçülmüştür.


* **Reranking:** Basit embedding (Bi-Encoder) hızlı filtreleme yaparken, Reranker (CrossEncoder) bağlamsal etkileşim ile en alakalı adayları en üste taşır.

## 🧩 Workflow Design (Figma)

![Workflow Note](assets/figma/workflow_note.png)

🔗 **Interactive Figma Board:**  
https://www.figma.com/board/f4OKvM7hf57WODcvAy3ei2/workflow_note?t=HOaMqdeYqSh3oXQB-1

## 🧠 Reasoning Architecture (Figma)

![Reasoning Board](assets/figma/reasoning.jpg)

🔗 **Interactive Figma Board:**  
https://www.figma.com/board/QfiHduJMe1jNs1H6xcBdbV/reasoning?node-id=0-1&t=j0kfZ2fZ5hvj66Kw-1




## 🛠️ Kurulum ve Kullanım

### Gereksinimler

* Python 3.x
* Agno Framework
* SQLite (Hafıza ve Storage için)
* Model API Anahtarları (Gemini, OpenAI veya Cohere) 
