Erweiterung des Monitor Scripts von Dustin1358 um eine Alarmdurchsage.
Die erweiterten bash Scripte sind im Ordner with_sound zu finden.

Das Script bezieht über die API nun auch die Variabeln $TITEL, $TEXT, $ADDRESSE und $NUMMER. Diese werden anschließend mittels picoTTS in eine Wave Datei verwandelt und lassen sich als "Alarmdurchsage" abspielen.

Im Aufruf des Programms pico2wave kann definiert werden welche Variabeln in welcher Reihenfolge abgespielt und welche Füllwörter gesprochen werden sollen.
Bei der Variable $TEXT ist zu beachten, dass die Formatierung und der Inhalt davon abhängt ob der Alarm manuell oder über eine Schnittstelle ausgelöst wurde und wie z.B. die Leitstelle ihre E-Mail formatiert.

Beim Verwenden der Variabel kann daher die "Bash Parameter Expansion" verwendet werden um den gesprochenen Text auf den gewünschten Teil zu beschränken. Im Script wird die Variabel mit `${TEXT%%<*}` aufgerufen da der Text in HTML formatiert ist und nur die erste Zeile vorgelesen werden soll.
Der Inhalt der Variable `$TEXT` wäre z.B. `Flächenbrand im Wald <br /> ---Fahrzeuge--- Florian Musterstadt 14-11-01` und würde mit dem Aufruf `${TEXT%%<*}` auf `Flächenbrand im Wald` gekürzt werden.

Um die Geschwindigkeit der Durchsage zu regulieren, wird die erstellte wave Datei mittels des Programms sox etwas verlangsamt.

Vor der eigentlichen Durchsage kann auch eine andere wave Datei als eine Art Alarmgong abgespielt werden.

Die erstellten wave Dateien der Alarme werden nach Beendigung der Durchsage mit der Alarmnummer versehen und gespeichert. Dies ist vorallem für Test Zwecke nützlich.

Die Durchsage wird momentan nur einmal abgespielt, wer möchte kann das ganze natürlich für sich selbst z.B. mit einer for-Schleife abändern.

Ich garantiere nicht, dass das Script zu 100% funktioniert.
