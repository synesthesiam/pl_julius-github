# Opis

HMM DNN Binarne polskie modele mowy (słownik 262K, 32-bitowy LM)

Aby korzystać z tych modeli, potrzebujesz zmodyfikowanej wersji Julius z:
https://github.com/palles77/julius

Możesz użyć prekompilowanej wersji Julius dla eksperymentów Windows "julius-dnn.exe" (może być konieczne zainstalowanie najnowszej wersji VC REDIST x86 z https://support.microsoft.com/en-gb/help/2977003/the-latest-supported-visual-c-downloads). W przeciwnym razie musisz pobrać kod źródłowy z powyższego adresu (https://github.com/palles77/julius), skonfigurować go i skompilować za pomocą VS 2017 lub GCC.

Aby skompilować z użyciem GCC możesz to zrobić na przykład jako:
$ bash configure --enable-words-int --enable-sp-segment
$ make all
$ make install

# Jak uruchamiać

julius-dnn -C julius.jconf -dnnconf dnn.jconf> julius-dnn-output.txt

Uwaga:
1. Ta kompilacja ma dyrektywę prekompilatora WORDS_INT ustawioną na 1 (która umożliwia stosowanie 32-bitowe modeli językowych).
2. Specjalna dyrektywa DNN jest ustawiona na 1 w libsent / include / sent / stddefs.h, aby umożliwić kompatybilność z modelami akustycznymi opartymi na DNN HTK obliczanie cech MFCC.

# Pliki w tym katalogu

dnn.jconf                     - plik konfiguracyjny DNN
PLPL-v7.1.am                  - 16 rozkładów Gaussa dla zwykłych trójfonów, model 32 rozkładowy ciszy, format binarny
PLPL-v7.1.dct                 - słownik wymowy
PLPL-v7.1.layer2_bias.npy     - zakłócenie warstwy 2
PLPL-v7.1.layer2_weight.npy   - wagi warstwy 2
PLPL-v7.1.layer3_bias.npy     - zakłócenie w warstwie 3
PLPL-v7.1.layer3_weight.npy   - wagi warstwy 3
PLPL-v7.1.layer4_bias.npy     - zakłócenie warstwy 4
PLPL-v7.1.layer4_weight.npy   - wagi warstwy 4
PLPL-v7.1.layer5_bias.npy     - zakłócenie warstwy 5
PLPL-v7.1.layer5_weight.npy   - wagi w warstwie 5
PLPL-v7.1.layer6_bias.npy     - zakłócenie warstwy 6
PLPL-v7.1.layer6_weight.npy   - wagi w warstwie 6
PLPL-v7.1.layerout_bias.npy   - zakłócenie warstwy wyjściowej
PLPL-v7.1.layerout_weight.npy - wagi warstwy wyjściowej
PLPL-v7.1.lm                  - model języka binarnego
PLPL-v7.1.mfc                 - dane standaryzacyjne mfc
PLPL-v7.1.norm                - dane normalizacyjne
PLPL-v7.1.phn                 - lista trójfonów w formacie binarnym
PLPL-v7.1.prior               - prawdopodobieństwa warstwy wyjściowej do obliczania klasyfikacji trójfonów
julius-dnn-output.txt         - przykładowy wynik dekodowania
julius-dnn.exe                - plik wykonywalny zmodyfikowany Julius skompilowany dla systemu Windows
julius.jconf                  - konfiguracja juliusa
lem.wav                       - przykładowy plik wave
README.Polish.md              - ten plik
README.English.md             - opis po angielsku
test.dbl                      - lista plików do dekodowania
wav_config                    - format pliku wejściowego do dekodowania (dane konfiguracyjne MFCC)

# Dodatkowe informacje

Szczegółową dokumentację można znaleźć na stronie głównej dekodera Julius
https://github.com/julius-speech/julius

Akceptowany format pliku to 16kHz, RIFF WAV PCM 16 bit, mono, liczba całkowita ze znakiem.
Dekodowany plik można zmienić edytując list.dbl

# Licencja
https://en.wikipedia.org/wiki/Mozilla_Public_License

# Kontakt
silesiaresearch małpa gmail kropka com

# Ostatnia zmiana
14 kwietnia 2018
