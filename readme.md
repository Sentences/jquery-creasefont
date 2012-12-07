# jQuery.creaseFont
jQuery.creaseFont is a Plugin for jQuery to resize the Font on the whole Page or only in some Elemements.

Start using creaseFont with default settings looks like this: 

	<script type="text/javascript" src="http://code.jquery.com/jquery-1.6.4.min.js"></script>
	<script type="text/javascript" src="jquery.creaseFont.min.js"></script>
	<script type="text/javascript">
	jQuery(document).ready(function(){
  		$.creaseFont();
	});
	</script>

The Buttons somewhere in the HTML body: 

	<span id="fontLarge" style="cursor:pointer">( + )</span>
	<span id="fontDefault" style="cursor:pointer">( &#216; )</span>
	<span id="fontSmall" style="cursor:pointer">( - )</span>

You can use every HTML Element with a proper ID.

**Options** 

You can use parameters in the following way, shown are the default settings: 

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

**Explanation:**

<table>
<thead style="font-weight: bold;">
<tr>
<td>
Param
</td>
      
      <td>
        Value
      </td>
    </tr>
  </thead>
  
  <tbody>
    <tr>
      <td>
        content
      </td>
      
      <td>
         	Can be one or more proper HTML Element.
			‘body’ is the whole HTML Document.
			‘#id’ proper ID of a Container.
			['#id1','id2'] ID’s of more than one Container in a Array.
			You can use any Selector like ['div.class > ul > li > a']
      </td>
    </tr>
    
    <tr>
      <td>
        default_size
      </td>
      
      <td>
        Default font size.<br />Default is 100%
      </td>
    </tr>
    
    <tr>
      <td>
        maxSize
      </td>
      
      <td>
        Maximum font size.<br />Default is 160%
      </td>
    </tr>
    
    <tr>
      <td>
        minSize
      </td>
      
      <td>
        Minimum font size.<br />Default ist 60%
      </td>
    </tr>
    
    <tr>
      <td>
        stepSize
      </td>
      
      <td>
        In this step the font size increases or decreases.<br />Defaut is 10%
      </td>
    </tr>
    
    <tr>
      <td>
        unit
      </td>
      
      <td>
        The unit of the font size.<br />Default is %.<br />Possible is %, em, px, pt (look at the examples)
      </td>
    </tr>
    
    <tr>
      <td>
        bFontLarge
      </td>
      
      <td>
        Unique ID of the button to increase.<br />
		Default is #fontLarge
      </td>
    </tr>
    
    <tr>
      <td>
        bFontDefault
      </td>
      
      <td>
        Unique ID of the button for default size.<br />
		Default is #fontDefault
      </td>
    </tr>
    
    <tr>
      <td>
        bFontSmall
      </td>
      
      <td>
        Unique ID of the button to decrease.<br />
		Default is #fontSmall
      </td>
    </tr>
    
    <tr>
      <td>
        animate
      </td>
      
      <td>
        Using Animation?<br />
		Default is true
      </td>
    </tr>
    
    <tr>
      <td>
        animateSpeed
      </td>
      
      <td>
        Animation Speed<br />
		Default is 500
      </td>
    </tr>
    
    <tr>
      <td>
        cookieName
      </td>
      
      <td>
        Name of the Cookie.<br />
		Default is creaseFont
      </td>
    </tr>
    
    <tr>
      <td>
        cookiePath
      </td>
      
      <td>
        Path for the Cookie.<br />
		Default is / for the whole Domain.
      </td>
    </tr>
    
    <tr>
      <td>
        cookieLifetime
      </td>
      
      <td>
        Lifetime of the Cookie in days.<br />
		Default is 60
      </td>
    </tr>
  </tbody>
</table> 

You can use a callback function at least Parameter, which will be called after the font size is increased, decreased or set to default. 

	$.creaseFont({
               after:function( obj ) {
                 $('#callback').html("Zoomlevel: " + obj.currSize + obj.currUnit + "&lt;br /&gt;Current Task: " + obj.currTask + "&lt;br /&gt;" + obj.currLvl);
                 }
               });
The object contains the following values. 

<table>
  <thead style="font-weight: bold;">
    <tr>
      <td>
        Object
      </td>
      
      <td>
        Value
      </td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        obj.currSize
      </td>
      
      <td>
        The current font size.<br />int or float
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currUnit
      </td>
      
      <td>
        The current unit (%,em,pt,px)<br />string
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currContent
      </td>
      
      <td>
        The HTML Element that has been altered as given in content.<br />string
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currTask
      </td>
      
      <td>
         	The current task that has been called. (increaseFont|defaultFont|decreaseFont)<br />string
      </td>
    </tr>
    
    <tr>
      <td>
        obj.currLvl
      </td>
      
      <td>
         	The current zoolevel that has been arrived or an empty String<br />
			max – Maximum zoomlevel arrived<br />
			default – Default zoomlevel has been clicked<br />
			min – The minimum zoomlevel has been arrived
      </td>
    </tr>
  </tbody>
</table>   

**Examples** 

Ein paar Beispiele mit Erläuterungen findet ihr hier: [jquery.creaseFont.js Plugin Example 1.][1] 

**Changelog** 

	1.0.3 - The callback function will now be called, after the animation is done
	1.0.2 - animate, animateSpeed added
	1.0.1 - First public release


 [1]: http://blog.mxtracks.de/projects/jQuery.creaseFont/example1.htm "jquery.creaseFont.js Plugin Example 1"