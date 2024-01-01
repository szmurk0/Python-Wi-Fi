# Python-Wi-Fi

Program do wypisywania haseł sieci Wi-Fi zapisanych na danym urządzeniu.


# Rzeczy potrzebne do włączenia programu

Potrzebne jest tylko i wyłącznie środowisko do Pythona, najlepiej IDLE. Subprocess to moduł, który jest częścią standardowej biblioteki Pythona, a więc nie trzeba go pobierać.


# Opis Kodu

- subprocess - Importuje moduł subprocess, który umożliwia wykonanie poleceń systemowych z poziomu Pythona.
  
- subprocess.check_output(['netsh', 'wlan', 'show', 'profiles']) - Uruchamia polecenie systemowe netsh wlan show profiles, aby uzyskać listę wszystkich dostępnych profili sieci Wi-Fi na komputerze.
  
- decode('latin-1').split('\n') - Dekoduje wynik polecenia z formatu bajtów do ciągu znaków (używając kodowania Latin-1) i dzieli go na linie.
  
- profiles = [i.split(":")[1][1:-1] for i in data if "All User Profile" in i] - Przetwarza wyniki, aby uzyskać tylko nazwy profili sieci Wi-Fi.
  
- Następnie, dla każdego profilu, wykonuje polecenie netsh wlan show profile <nazwa_profilu> key=clear, aby uzyskać szczegóły dotyczące danego profilu, w tym klucz (hasło).
  
- results = [b.split(":")[1][1:-1] for b in results if "Key Content" in b] - Przetwarza wyniki, aby uzyskać tylko zawartość klucza (hasła).
  
- W bloku try-except drukuje nazwę profilu i odpowiadające mu hasło. W przypadku braku hasła, zostanie wydrukowany pusty ciąg znaków.
  
- input("Naciśnij Enter aby wyjść...") - Oczekuje na naciśnięcie klawisza Enter, aby program się zakończył.
