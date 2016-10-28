# Trep-validator
Valideringsfiler för Trep kalkyl

Ett första utkast.

## Vad är Trep-validator?
Trep är ett gratis och webbaserat kalkylprogram för elinstallationer. Kalkylerna gör du i webbläsaren på datorn, i surfplattan eller telefonen.<br>
Trep validator (Validatorn) är en del av kalkylprogrammet Trep.<br>
Validatorn validerar användarens kalkyl för att fastställa om något som borde finnas med i kalkyl saknas.

## Användningsområde

## Valideringsmodell
Modellen som används i koden är en fråga typ:<br>
<br>Finns X och/eller Y? Borde inte Z isåfall finnas?<br><br>
Ett verkligt exempel skulle kunna vara:<br>
Finns golvstativ eller väggstativ? Borde det inte finnas patchpanel?<br>

## Kodexempel

## Valideringsfilen

## Bidra


Modellen som används är en fråga typ:
<br>Finns X eller/och Y? Borde inte Z finnas?

### Joomla

**Menu Editor**

[**Learn More**](http://docs.gantry.org/gantry5/configure/gantry-admin)

`-update`

[GPL version 2 or later](http://www.gnu.org/licenses/old-licenses/gpl-2.0.html)

|:-----------------------------------------------------------------------:|

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
