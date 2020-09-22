<div align="center">

## Templates Made Easy\!


</div>

### Description

This is an introduction to templates and their uses. Easy to learn! You should be familiar with functions and classes.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Andrew Hull](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/andrew-hull.md)
**Level**          |Intermediate
**User Rating**    |4.8 (24 globes from 5 users)
**Compatibility**  |C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/andrew-hull-templates-made-easy__3-2985/archive/master.zip)





### Source Code

<H2><CENTER><FONT FACE="Georgia">Templates Made Easy</FONT></CENTER></H2>
<P>&nbsp;</P>
<P><FONT FACE="Times New Roman">So, what exactly is a template?
You've probably heard the word before, perhaps you've had experience
with the STL, or Standard Template Library. So what makes templates
so important and useful? Let's consider a simple swap function
to exchange 2 values:</FONT></P>
<P><B>void Swap(int &amp;A, int &amp;B)<BR>
{<BR>
int Temp = A;<BR>
A = B;<BR>
B = Temp;<BR>
}</B></P>
<P><FONT FACE="Times New Roman">This functions takes the address
of 2 int's and swaps their values. Now, what happens if you want
to swap 2 chars? Easy, you can overload the Swap() function:</FONT></P>
<P><B>void Swap(char &amp;A, char &amp;B)<BR>
{<BR>
char Temp = A;<BR>
A = B;<BR>
B = Temp;<BR>
}</B></P>
<P><FONT FACE="Times New Roman">You can keep overloading for every
primitive data type there is (int, char, float, double, bool,
etc). However, what if you want to swap 2 objects? What if your
program has 10 different types of objects, all of which need to
be swapped? It seems like a lot of work to keep writing overloaded
Swap() functions for every type you want to swap. Isn't there
some way to create an &quot;outline&quot;, or <I>template </I>to
describe a generic Swap() function that will work for ANY data
type? The syntax for a templated function is:</FONT></P>
<P><B>template &lt;class <I>type</I>&gt;<BR>
<I>return_type function_name</I> (<I>parameters</I>)<BR>
{<BR>
// function body<BR>
}</B></P>
<P><FONT FACE="Times New Roman">&quot;T&quot; is the most often
used class name for template. (T = type). So, here is the Swap()
function, this time with a template:</FONT></P>
<P><B>template &lt;class T&gt;<BR>
void Swap(T &amp;A, T &amp;B)<BR>
{<BR>
T Temp = A;<BR>
A = B;<BR>
B = Temp;<BR>
}</B></P>
<P><FONT FACE="Times New Roman">template defines T to be a generic
data type- it will be filled in later when the function is called.
The parameters A and B are of type T, meaning their type will
be filled in later. This is the syntax for calling our Swap()
function, as well as any templated function:</FONT></P>
<P><B>int a = 1, b = 2;<BR>
Swap&lt;int&gt;(a, b);</B></P>
<P><FONT FACE="Times New Roman">The compiler translates this to:</FONT></P>
<P><B>void Swap(int &amp;A, int &amp;B)<BR>
{<BR>
int Temp = A;<BR>
A = B;<BR>
B = Temp;<BR>
}</B></P>
<P><FONT FACE="Times New Roman">Here is the syntax for calling
with char values:</FONT></P>
<P><B>char a = 'a', b = 'b';<BR>
Swap&lt;int&gt;(a, b);</B></P>
<P><FONT FACE="Times New Roman">This becomes:</FONT></P>
<P><B>void Swap(char &amp;A, char &amp;B)<BR>
{<BR>
char Temp = A;<BR>
A = B;<BR>
B = Temp;<BR>
}</B></P>
<P><FONT FACE="Times New Roman">See the pattern? The value given
to the function in the &lt;&gt; brackets replaces T in the function
definition. Now, here's where the real usefulness of templates
comes in: classes. Say you make a simple list function that you
want to hold any type of data: primitive types or class objects.
You'll be distributing the code and you don't know what objects
will be put into your list. You can apply the template keyword
to your class and its member functions to create objects that
can hold any data type! Take this example of the list class:</FONT></P>
<P><B>template &lt;class T&gt;<BR>
class List<BR>
{<BR>
public:<BR>
void AddItem(T item);<BR>
void DeleteItem(T item);<BR>
void ShowItems();<BR>
private:<BR>
T* list;<BR>
};</B></P>
<P><B>template &lt;class T&gt;<BR>
void List::AddItem(T item)<BR>
{<BR>
// ...<BR>
}</B></P>
<P><B>template &lt;class T&gt;<BR>
void List::DeleteItem(T item)<BR>
{<BR>
// ...<BR>
}</B></P>
<P><B>template &lt;class T&gt;<BR>
void List::ShowItems()<BR>
{<BR>
// ...<BR>
}</B></P>
<P><FONT FACE="Times New Roman">And so on...</FONT></P>
<P><FONT FACE="Times New Roman">You can see that T will be replaced
by whatever data type is given to the object. the template keyword
needs to be put before the class declaration as well as each function
definition. Here is the syntax creating a List object:</FONT></P>
<P><B>List&lt;int&gt; myList;</B></P>
<P><FONT FACE="Times New Roman">This creates a List of int's.
All T's in the class and functions are replaced by int. Now, let's
say you have a simple struct like this:</FONT></P>
<P><B>struct data<BR>
{<BR>
int a;<BR>
double b;<BR>
char c;<BR>
};</B></P>
<P><FONT FACE="Times New Roman">And you want to make a list of
data's. With a template, it's easy!</FONT></P>
<P><B>List&lt;data&gt; myList;</B></P>
<P><FONT FACE="Times New Roman">And you have a List of data's!</FONT></P>
<P><FONT FACE="Times New Roman">-----------------------------------------------------------------------------------------------</FONT></P>
<P><FONT FACE="Times New Roman">I hope you've learned something
from this! Please leave any comments/feedback that come to mind,
everything is appreciated! If you need anything cleared up, feel
free to email me at kavutitan26@yahoo.com. Enjoy!</FONT></P>
<P><FONT FACE="Times New Roman">-&gt; Andrew &lt;-</FONT>

