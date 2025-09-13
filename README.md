# AskMate – Chrome Extension (MV3)

Scan halaman web saat ini, ekstrak teksnya, lalu kirim ke Gemini (2.5 Flash/Pro) dengan opsi Thinking/non-Thinking. Hasil akan ditampilkan sebagai overlay di halaman.

## Screenshoots
<img width="1469" height="906" alt="image" src="https://github.com/user-attachments/assets/ca9e9a97-67f3-4720-bab0-b0fe3a4f6ee0" />
<img width="1277" height="867" alt="image" src="https://github.com/user-attachments/assets/4ac55985-5284-45b6-88c8-e64bed7aec41" />


## Fitur Utama
- Enabled current tab absolute right click & copy when Scan Current Tab button triggered!
- Fast Action using shortcut: CTRL + SHIFT + F (to ask current web, based on extension setting preferences!)
- Search/Crawling web using GeminiAPI
- Toggle: auto hide/use legacy style (non glass ui)

## Misc
- Input dan simpan Gemini API Key (chrome.storage.sync)
- Pilihan model: 2.5 Flash, 2.5 Pro, Flash-Lite, dan Flash Preview
- Thinking toggle: Smart / Fast
- Tombol Scan mengekstrak teks dari tab aktif dan memanggil Gemini API
- Hasil ditampilkan sebagai overlay mengambang di halaman
 

## Cara Pakai

1. Dapatkan API Key Gemini dari Google AI Studio.
2. Buka Chrome > Manage Extensions > aktifkan Developer Mode.
3. Klik "Load unpacked" dan pilih folder `AskMate/`.
4. Buka popup AskMate:
   - Masukkan API Key, pilih model, atur Thinking (Off/Dynamic/Custom), klik Save.
   - Klik "Scan Current Tab" untuk menjalankan.
5. Lihat hasil di overlay di halaman.

## Catatan Integrasi Gemini

- Endpoint REST: `POST https://generativelanguage.googleapis.com/v1beta/models/{model}:generateContent`
- Header: `x-goog-api-key: <API_KEY>`, `Content-Type: application/json`
- Payload minimal:

```json
{
  "contents": [
    { "parts": [ { "text": "Your prompt here" } ] }
  ],
  "generationConfig": {
    "thinkingConfig": { "thinkingBudget": 0 }
  }
}
```

- Thinking:
  - Off: `thinkingBudget = 0`
  - Dynamic: `thinkingBudget = -1` 

Sumber: Dokumentasi resmi Gemini API (ai.google.dev).
