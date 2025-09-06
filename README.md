use C++17 + pybind11 -> core BE logic in C++17 and then we have pybind11 to use the executables (C++ BE and Python as instrumental module)
use RtAudio to capture audio from a sound source
Whisper.cpp to use the captured audio for text
Then use Marian-NMT for translations

Video File
    │
    ▼
C++ (RtAudio) → captures audio → stores buffer
    │
    ▼
C++ (Whisper.cpp) → transcribes → produces text + timestamps
    │
    ▼
C++ (Marian-NMT) → translates → produces translated text
    │
    ▼
Python → receives translated text → outputs subtitle file or TTS


[Video File / System Audio]
          │
          ▼
   C++17 + RtAudio
    Capture audio
          │ (buffered chunks)
          ▼
   C++17 + Whisper.cpp
    Transcription
          │ (Transcription structs)
          ▼
   C++17 + Marian-NMT
    Translation
          │ (Translation structs)
          ▼
      Python layer
    Orchestration & Output
     → Subtitles / JSON / TTS
