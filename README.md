# StringFormat
#include &lt;Date.au3> Func _StringFormatMs($ms, $bRetMs = False) ; based on https://www.autoitscript.com/forum/topic/163621-convert-ms-to-dayhourminsec/?do=findComment&amp;comment=1192334     Local $sRetMs = "", $day = "", $hour, $min, $sec     _TicksToTime($ms, $hour, $min, $sec)     If $hour >= 24 Then         $day = Int($hour / 24)         $hour = Mod($hour, 24)     EndIf     If $bRetMs Then $sRetMs = "." &amp; StringRight($ms, 3)     Switch StringLen($day)         Case 0             Return StringFormat("%02i:%02i:%02i", $hour, $min, $sec) &amp; $sRetMs         Case 1, 2, 3             Return StringFormat("%03i %02i:%02i:%02i", $day, $hour, $min, $sec) &amp; $sRetMs         Case Else             Return $day &amp; " " &amp; StringFormat("%02i:%02i:%02i", $hour, $min, $sec) &amp; $sRetMs     EndSwitch
