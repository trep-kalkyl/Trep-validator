# Trep-validator
Valideringsfiler för Trep kalkyl

Valideringsfiler används för att validera riktigheten i kalkyler.

Ett första utkast.


## Accessing the Gantry Administrator 

Modellen som används är en fråga typ:
<br>Finns X eller/och Y? Borde inte Z finnas?

Som verkligt exempel:<br>Finns Golvstativ eller väggstativ? Borde det inte finnas patchpanel?

Valideringsfilen validerar och kontrollerar alltså om det är möjligt att användaren glömt nåt i sin kalkyl.

I valideringsfilen ter sig det uttrycket så här:

<!-- Finns Golvstativ eller väggstativ? Borde det inte finnas patchpanel? --> 
		<item>
			<search>(\b(GOLVSTATIV|VÄGGSTATIV)\b.*?)\bVALIDERINGSKONTROLL DATA 1 EJ TILLÄMPLIG\b</search>
			<replace>\1<![CDATA[with <u><p><strong><font size="3" color="Red">VALIDERINGSKONTROLL DATA 1 UTFÖRD MED NOTERING: Datastativ saknar patchpanel</font></strong></p></u>]]></replace>
		</item>
		<item>
			<search>((PATCHPANEL<!-- kalkylartikelsvalidering -->).*?)\bVALIDERINGSKONTROLL DATA 1 UTFÖRD MED NOTERING\: Datastativ saknar patchpanel\b</search>
			<replace>\1<![CDATA[with <u><p><strong><font size="3" color="Green">OK! Valideringskontroll data 1 utförd utan notering</font></strong></p></u>]]></replace>
		</item>		
