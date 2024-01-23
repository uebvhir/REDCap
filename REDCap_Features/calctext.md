<h3>@<span style="text-decoration: underline;">CALCTEXT</span></h3>
<p>Evaluates logic that is provided inside a @CALCTEXT() function and outputs the<br>result as text, typically performed with an if(x,y,z) function - e.g.,<br>@CALCTEXT(if([gender]='1', 'male', 'female')). NOTE: It is important to realize<br>that a field with @CALCTEXT will not be editable on the survey page or data<br>entry form, and the field will function almost exactly like a normal calculated<br>field, in which its value may get updated via a data import, when running Data<br>Quality rule H, or in real-time during normal data entry on a form or survey. If<br>desired, it is possible to return the value as a number - e.g., @CALCTEXT(if([age]<br>&gt;= 18, 'adult', 5*[other_field])). Also, while it is possible to use static text (in<br>quotes), field variables, or Smart Variables as the return values of the IF function<br>- e.g., @CALCTEXT(if([age] &gt;= 18, [dob], [event-label]) - it is NOT possible to pipe<br>field variables or Smart Variables inside quotes for the return values.</p>
<p>-----------------------</p>
<p>Calculated fields can only return numerical values. You should use a calculated field any time you want REDCap to give you back a number, such as calculating a BMI or the number of days between two dates. Calculated fields always return numbers.</p>
<p>You can find more information about using calculations in the "Calculations" section of the FAQ and by using the "How do I format the equation" link when you create a calculated field in the Online Designer. Calculated fields always return numbers.</p>
<p>@CALCTEXT is an action tag you can use on a text field that can return a text value. For example, you can use this if you have an "if" statement and you want REDCap to display the word "TRUE" if the result is true and "FALSE" if the result is false. @CALCTEXT always returns text.</p>
<p>You can find more details on setting up @CALCTEXT by clicking on the red "Action Tags" button on the Project Setup page, editing a form in the Online Designer, or when editing a field.</p>
<p>@CALCDATE is an action tag you can use on text field that is validate as a date or datetime. It will calculate a date or datetime a specific amount of time away from a date you give it. For example, if you know the discharge date and want to schedule a follow up ten days later, you can use @CALCDATE to tell you what day the follow up should be. @CALCDATE always returns a date.</p>
<p>You can find more details on setting up @CALCDATE by clicking on the red "Action Tags" button on the Project Setup page, editing a form in the Online Designer, or when editing a field.</p>
<p>--------------</p>
<p>If the result of concatenating multiple text fields SHOULD NOT be editable, use the @CALCTEXT Action Tag with the concat special function. For example, to concatenate first and last name, with a space between them:</p>
<p>@CALCTEXT(concat([first_name], ' ', [last_name]))</p>
<p> </p>
<p>If the result of concatenating multiple text fields SHOULD be editable, then use the @DEFAULT Action Tag. For example, to concatenate first and last name, with a space between them, but allow the result to be edited:</p>
<p>@DEFAULT="[first_name] [last_name]"</p>
<p>------------------------</p>
<p>Data entry via forms or surveys will cause calculations to be performed in the same form or survey during data entry. The results of these calculations will only be saved to REDCap if the form is saved or if a survey is continued/submitted.</p>
<p> </p>
<p>Data entry via forms or surveys can cause cross-form and cross-event calculations, in which calculated fields and @CALCTEXT fields in other forms and in other events are potentially updated. The cross-form and cross-event calculations will be performed and saved when the original form or survey is saved/continued/submitted.</p>
<p> </p>
<p>Similarly, data imports via the Data Import Tool or the API can cause auto-calculations, in which calculated fields and @CALCTEXT fields in the same form, in other forms, and in other events are potentially updated. Auto-calculations will be performed and saved when the data being imported are saved.</p>
<p> </p>
<p>Cross-form calculations, cross-event calculations, and auto-calculations are performed for calculated or @CALCTEXT fields in which:</p>
<ul>
<li>the calculation logic refers to another field that has changed, OR</li>
<li>the calculation logic uses the 'if()' statement and both output options in the 'if()' statement are non-blank, implying that the field should always have a value.</li>
</ul>
<p> </p>
<p>Cross-event calculations and auto-calculations are only performed in events which have any fields that already contain data. This is true of cross-form calculations as well, but by definition cross-form calculations only occur when an event has data.</p>
