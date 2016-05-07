# Javon expression operators precedence

<table width="90%" bordercolor="#111111" style="BORDER-COLLAPSE: collapse" border="1" cellspacing="0" cellpadding="2">
        
        <tbody><tr>
          <th>
            <p align="center"><b>Operator</b></p></th>
          <th><b>Description</b></th>
          <th>
            <p align="center"><b>Associativity</b></p></th></tr>
        <tr>
          <td align="center"><font size="2">( )<br>[ ]<br>.<br>#<br>?. ?#<br>++ --</font></td>
          <td><font size="2">Parentheses (function call) 
            (nest expression group)
            <br>Brackets (array subscript)<br>Member selection via object name
            <br>Cast (convert value to temporary value of <i>type</i>)
            <br>conditional selecting or converting
            <br>Postfix increment/decrement</font></td>
          <td valign="top">
            <p align="center"><font size="2">left-to-right</font></p></td></tr>
        <tr>
          <td align="center"><font><font size="2"><font>++ 
            --<br>+ -<br>! ~</font> </font></font></td>
          <td><font size="2">Prefix increment/decrement<br>Unary plus/minus<br>Logical negation/bitwise complement
          </font></td>
          <td align="center" valign="top"><font size="2">right-to-left</font></td></tr>
        <tr>
          <td align="center"><font size="2">* &nbsp;/&nbsp; %</font></td>
          <td><font size="2">Multiplication/division/modulus</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">+ &nbsp;-</font></td>
          <td><font size="2">Addition/subtraction</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">&lt;&lt;&nbsp; &gt;&gt; &nbsp; &gt;&gt;&gt;</font></td>
          <td><font size="2">Bitwise shift left, Bitwise shift right, Bitwise unsigned shift right</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">&lt;&nbsp; &lt;=<br>&gt;&nbsp; &gt;=</font></td>
          <td><font size="2">Relational less than/less than 
            or equal to<br>Relational greater than/greater 
            than or equal to</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">== &nbsp;!=</font></td>
          <td><font size="2">Relational is equal to/is not 
            equal to</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">&amp;</font></td>
          <td><font size="2">Bitwise AND</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">^</font></td>
          <td><font size="2">Bitwise exclusive OR</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">|</font></td>
          <td><font size="2">Bitwise inclusive OR</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">&amp;&amp;</font></td>
          <td><font size="2">Logical AND</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">| |</font></td>
          <td><font size="2">Logical OR</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">,<br>..</font></td>
          <td><font size="2">Separator for element of array<br>range(e.g. 1..100)</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td align="center"><font size="2">? :<br>?! : <br>@?: :<br>@?! : :</font></td>
          <td><font size="2">
          Single/Ternary/Switch conditional
          <br>same as above, simplify the !() case
          <br>loop
          <br>same as above, simplify the !() case
          </font></td>
          <td align="center" valign="top"><font size="2">right-to-left</font></td></tr>
        <tr>
          <td align="center"><font size="2">=<br>+= &nbsp;-=<br>*=&nbsp; /=<br>%=&nbsp; 
            &amp;=<br>^=&nbsp; |=<br>&lt;&lt;=&nbsp; &gt;&gt;=</font></td>
          <td><font size="2">Assignment<br>Addition/subtraction assignment<br>Multiplication/division assignment<br>Modulus/bitwise AND assignment<br>Bitwise exclusive/inclusive OR assignment<br>Bitwise shift left/right assignment</font></td>
          <td align="center" valign="top"><font size="2">right-to-left</font></td></tr>
        <tr>
          <td>
            <p align="center"><font size="2">:</font></p></td>
          <td><font size="2">Colon (@label)</font></td>
          <td align="center" valign="top"><font size="2">left-to-right</font></td></tr>
        <tr>
          <td colspan="3">
            </td></tr></tbody></table>
