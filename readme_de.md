# jQuery.creaseFont
ist ein Plugin für jQuery um die Schriftgröße auf der gesamten Homepage oder nur Teile davon zu vergrößern oder zu verkleinern. Ich hab aus meinem jQuery Workaround nun ein Plugin geschrieben. Das ist flexibler. 

Die Einbindung mit den default settings sieht folgendermaßen aus. Weitere Beispiele mit Einstellungen folgen weiter unten. HTML Head bereich: 

	<script type="text/javascript" src="http://code.jquery.com/jquery-1.6.4.min.js"></script>
	<script type="text/javascript" src="jquery.creaseFont.min.js"></script>
	<script type="text/javascript">
	jQuery(document).ready(function(){
  		$.creaseFont();
	});
	</script>

Nun Beispielsweise noch die Buttons folgendermaßen einfügen: 

	<span id="fontLarge" style="cursor:pointer">( + )</span>
	<span id="fontDefault" style="cursor:pointer">( &#216; )</span>
	<span id="fontSmall" style="cursor:pointer">( - )</span>

Als Button kann jedes Element mit der passenden ID genutzt werden. 

**Optionen** 

Folgende Parameter können dem Aufruf übergeben werden. Die hier gezeigten, sind auch die Standardparameter: 

	$.creaseFont({
              content     :  'body',
              defaultSize :  100,
              maxSize     :  160,
              minSize     :  60,
              stepSize    :  10,
              unit        :  '%',
              bFontLarge  :  '#fontLarge',
              bFontDefault:  '#fontDefault',
              bFontSmall  :  '#fontSmall',
              animate     :  true,
              animateSpeed:  500,
              cookieName  :  'creaseFont',
              cookiePath  :  '/',
              cookieLifetime:60
              });
	});

**Erläuterung:**

<table>
<thead style="font-weight: bold;">
<tr>
<td>
Parameter
</td>
      
      <td>
        Wert
      </td>
    </tr>
  </thead>
  
  <tbody>
    <tr>
      <td>
        content
      </td>
      
      <td>
        Kann ein oder mehere beliebige Elemente enthalten. 'body' bezeichnet das gesamte Dokument und ist default. '#id' die id eines bestimmten Containers ['#id1','id2'] die ID's mehrerer Container in einem Array.
      </td>
    </tr>
    
    <tr>
      <td>
        default_size
      </td>
      
      <td>
        Standardschriftgröße. Default ist 100%
      </td>
    </tr>
    
    <tr>
      <td>
        maxSize
      </td>
      
      <td>
        Maximale Schriftgröße. Default ist 160%
      </td>
    </tr>
    
    <tr>
      <td>
        minSize
      </td>
      
      <td>
        Minimale Schriftgröße. Default ist 60%
      </td>
    </tr>
    
    <tr>
      <td>
        stepSize
      </td>
      
      <td>
        Um diesen Wert wird die Schrift vergrößert oder verkleinert. Defaut ist 10%
      </td>
    </tr>
    
    <tr>
      <td>
        unit
      </td>
      
      <td>
        Die Einheit der Schrift. Default ist % Möglich ist %, em, px, pt (beachte die Beispiele)
      </td>
    </tr>
    
    <tr>
      <td>
        bFontLarge
      </td>
      
      <td>
        Eindeutige ID des Buttons für die Vergrößerung. Default ist #fontLarge
      </td>
    </tr>
    
    <tr>
      <td>
        bFontDefault
      </td>
      
      <td>
        Eindeutige ID des Buttons für die Standardgröße. Default ist #fontDefault
      </td>
    </tr>
    
    <tr>
      <td>
        bFontSmall
      </td>
      
      <td>
        Eindeutige ID des Buttons für die Verkleinerung. Default ist #fontSmall
      </td>
    </tr>
    
    <tr>
      <td>
        animate
      </td>
      
      <td>
        Animation einschalten? Default ist true
      </td>
    </tr>
    
    <tr>
      <td>
        animateSpeed
      </td>
      
      <td>
        Geschwindigkeit für die Animation Default ist 500
      </td>
    </tr>
    
    <tr>
      <td>
        cookieName
      </td>
      
      <td>
        Name des Cookies, in dem die Werte gespeichert werden. Default ist creaseFont
      </td>
    </tr>
    
    <tr>
      <td>
        cookiePath
      </td>
      
      <td>
        Pfad in dem das Cookie gültig ist. Default ist / für die gesamte Domain.
      </td>
    </tr>
    
    <tr>
      <td>
        cookieLifetime
      </td>
      
      <td>
        Dauer der gültigkeit des Cookies in Tagen. Default ist 60
      </td>
    </tr>
  </tbody>
</table> 

Als letzten Parameter könnt ihr eine Callback Funktion aufrufen, welche ausgeführt wird, nachdem die Schrift vergrößert, verkleinert oder zurückgesetzt wurde. 

	$.creaseFont({
               after:function( obj ) {
                 $('#callback').html("Zoomlevel: " + obj.currSize + obj.currUnit + "&lt;br /&gt;Current Task: " + obj.currTask + "&lt;br /&gt;" + obj.currLvl);
                 }
               });
Das Object beinhaltet folgende Werte. 

<table>
  <thead style="font-weight: bold;">
    <tr>
      <td>
        Object
      </td>
      
      <td>
        Wert
      </td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        obj.currSize
      </td>
      
      <td>
        Die aktuelle Schriftgröße. int oder float
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currUnit
      </td>
      
      <td>
        Die genutze Einheit (%,em,pt,px) string
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currContent
      </td>
      
      <td>
        Das HTML Element welches verändert wurde, wie bei content übergeben. string
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currTask
      </td>
      
      <td>
        Die aktuelle Aufgabe welche ausgeführt wurde. (increaseFont|defaultFont|decreaseFont) string
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currLvl
      </td>
      
      <td>
        Das aktuelle Zoomlevel welches erreicht wurde oder ein leerer String max - Maximale Zoolevel wurde erreicht default - Default Zoomlevel wurde geklickt min - Das minimale Zoomlevel wurde erreicht
      </td>
    </tr>
  </tbody>
</table>   

**Beispiele** 

Ein paar Beispiele mit Erläuterungen findet ihr hier: [jquery.creaseFont.js Plugin Example 1.][1] 

**Changelog** 

	1.0.3 - Die Callback Funktion wird nun erst ausgeführt, nachdem eine evtl. Animation beendet ist.
	1.0.2 - animate, animateSpeed hinzugefügt.
	1.0.1 - Erstes Public release


 [1]: http://blog.mxtracks.de/projects/jQuery.creaseFont/example1.htm "jquery.creaseFont.js Plugin Example 1"