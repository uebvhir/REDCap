<h3>@<span style="text-decoration: underline;">ACTION @TAGs: CALCTEXT</span></h3>
<p> </p>
<h6>Do you know what are Action Tags?</h6>
<p><em>'Action Tags are special terms that begin with the '@' sign that can be placed inside a field's Field Annotation' (see <a title="REDCap Help &amp; FAQ page" href="https://redcap.vhir.org/redcap/index.php?action=help" target="_blank" rel="noopener">REDCap Help &amp; FAQ page</a>.)</em></p>
<p><em><img src="https://github.com/uebvhir/REDCap/blob/35410e383f6dbd355f3874619ea8108ae3c27fdb/REDCap_Features/Imatges/action_tag.png" width="661" height="123"></em></p>
<p> </p>
<h6>@CALCTEXT()</h6>
<p>Function</p>
<ul>
<li><span style="font-weight: normal;">Evaluates the logic inside its brackets - </span>@CALCTEXT()<span style="font-weight: normal;"> - and outputs the result as text and/or number. </span>
<ul>
<li><span style="font-weight: normal;">It only works in <span style="text-decoration: underline;">'Text Box' field types</span>.</span></li>
</ul>
</li>
</ul>
<p><span style="font-weight: normal;"><img src="https://github.com/uebvhir/REDCap/blob/35410e383f6dbd355f3874619ea8108ae3c27fdb/REDCap_Features/Imatges/field_type.png" width="684" height="79"></span></p>
<ul>
<li><span style="font-weight: normal;">This annotated field will function <em>almost exactly</em> like a <span style="text-decoration: underline;">'Calculated Field' type</span>.</span></li>
</ul>
<p>Examples</p>
<ol>
<li><span style="font-weight: normal;">It can concatenate two (or more) fields with -as an example- a space between them:</span></li>
</ol>
<pre>@CALCTEXT(concat([first_field], ' ', [second_field]))</pre>
<ol start="2">
<li><span style="font-weight: normal;">It can be combined with a normal <span style="text-decoration: underline;"><em>if(x,y,z)</em> function</span>:</span></li>
</ol>
<pre>@CALCTEXT(if([your_field]='numeric-value', 'value if TRUE', 'Value if FALSE'))</pre>
<ol start="3">
<li><span style="font-weight: normal;">It can display the word "TRUE" if the result is true and "FALSE" if the result is false.</span></li>
</li>
</ol>
<pre>@CALCTEXT(if([your_field] &gt; 8, 'TRUE', 'FALSE'))</pre>
<pre>@CALCTEXT(if([smoke]='1', 'possible case', 'excluded'))<br>@CALCTEXT(if([background(1)]='1', 'possible case', 'excluded'))</pre>
<ol start="4">
<li><span style="font-weight: normal;">It is possible to insert 'static text', field variables, or Smart Variables as return values within the IF function:</span></li>
<ul>
<li><span style="font-weight: normal;">But, it is </span>NOT<span style="font-weight: normal;"> possible to<em> '[pipe]'</em> field variables or Smart Variables inside quotes for the return values.</span></li>
</ol>
<pre>@CALCTEXT(if([your_field] &gt;= 18, [other_field], [current-instance])</pre>
<ol start="5">
<li><span style="font-weight: normal;">it can return a value as a number:</span></li>
<pre>@CALCTEXT(if([one_field] &gt;= 180, 'out of range', 0.5*[other_field]))</pre>
<p>Notes</p>
<ul>
<li>CALCTEXT() <span style="font-weight: normal;">values can be updated when running <em><span style="text-decoration: underline;">Data Quality rule H</span></em> (see <span style="text-decoration: underline;">Data Quality page</span> of a REDCap project as follows):</span></li>
</ul>
<p><span style="font-weight: normal;"><img style="float: left;" src="https://github.com/uebvhir/REDCap/blob/35410e383f6dbd355f3874619ea8108ae3c27fdb/REDCap_Features/Imatges/data_quality.png" width="218" height="249"></span></p>
