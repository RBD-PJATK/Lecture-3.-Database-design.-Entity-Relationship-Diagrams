# Lecture 3. Database design. Entity-Relationship Diagrams

<h2 align="center">Lecture 3</h2>

<h2 align="center"><i>Database design - entity-relationship diagrams</i></h2>

<hr><h3>Abstract</h3>

<p>Lecture 3 is a presentation of the fundamental method of the development of
the schema of a relational database.  This method consists of two steps. 
During the first step we design the <i>data model</i> of the considered
application domain.  The second step is the conversion of this model to the
schema of the database.</p>

<p>Special software (<i>CASE</i> = Computer-Aided System Engineering) provides
tools to design and draw a diagram on the computer display.  It can also
generate automatically the schema of a database in a given database system
(e.g. Microsoft Access). This lecture exemplifies the new terms with snapshots
of screens produced by <u>Microsoft Visio (2000)</u> (a tool to draw various
diagrams; entity-relationship diagrams are among them).</p>

<p>You will find some exercises in the text. In order to
solve them you need Microsoft Visio or other software that
facilitates drawing.</p>

<hr><h3><a name="Projektowanie">Entity-relationship diagram</a></h3>

<p>The goals of the process of the design of the schema of a database are:

<ol>
<li>to specify user requirements of the prospective database and to analyze
	these requirements;
<li>to create the schema of a database which fulfills user requirements
	and guarantees proper functioning of the database inside the
	whole information system;
<li>to design the schema of the database.
</ol>
</p>

<p>In most cases before you create a database, you analyze the
information requirements and render them in the form of a data model called
<i>the entity-relationship diagram</i>.  This diagram abstracts from
technical details of the implementation in a given database system.</p>

<h4>Intermediate design model (the entity-relationship diagram)</h4>

<p>Intermediate design model should:

<ol>
<li>unambiguously state the user requirements in a way that allows users to
	check whether the analyst correctly understood the users' intents 
	and the specific character of the business of the company;
<li>be much simpler than the schema of the database, because it abstracts
	from the details of the implementation that have to be defined later by the
	designer.
</ol>

<p>We will describe subsequent elements of an entity-relationship diagram:
<i>entities</i>, <i>attributes</i> and <i>relationships</i>.</p>
 
<hr><h3><a name="Encja">Entity</a></h3>

<p><i>Entity</i> (object) is something that exists and can be distinguished from
other beings. Information about an entity must be known or stored.
Entities with the same properties constitute types (sets) of entities.
The graphical representation of and entity is a rectangular frame:

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_1.png"></p>

You should distinguish <i>the type of an entity</i> from <i>the instance of
an entity</i>, e.g. <i>Person</i> as a type and as a given object (Krzysztof
Stencel).</p>    

<hr><h3><a name="Atrybut">Attribute</a></h3>

<p><i>Attribute</i> is the property of entities of a given type. It is
represented as a certain value like an integer, a real number or a
string.</p>

<p>An attribute should characterize the entity it has been assigned to.  It
should not define a relationship to other entities.  For instance <i>the seat
number</i> in a theater is an attribute of the entity <i>Seat</i>, but it is not
an attribute of the entity <i>Ticket</i> where it also appears physically.</p>

<h4>First normal form (1NF)</h4>

<p>Every attribute of every instance of an entity should have a single atomic
value.  For this reason <i>Employee's children</i> must not be an attribute.
</p>

<h4>Derived attributes</h4>

<p>You should not create derived attributes, i.e. attributes whose values
can be computed from other data. For example <i>Age</i> can be deduced from
the <i>Birth date</i>.</p>

<hr><h3><a name="Klucz">Key</a></h3>

<p>A <i>key</i> (<i>unique identifier</i>)
is a set (may be a singleton) of attributes of the same entity such that
their values identify every instance of this entity. An entity
can have any number of keys.  One of these keys is designated to be
<i>primary</i> while the others are <a name="alternative-key"><i>alternative</i></a>.</p>

<p>The attributes of the primary key are labeled with PK and are underlined.
Alternative keys are marked by <a href="#idenksy-unikatowe">unique
indexes</a>.</p>

<p>Using MS Visio you indicate attributes on tab "Columns".  There are two
specifications of data types: <i>Portable Data Type</i> and
<i>Physical Data Type</i> (associated with a given database system):

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_2.png"></p>

Here is an example of physical data types for MS Access:

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_3.png"></p>

<p>(&quot;Req'd&quot; is an abbreviation of &quot;Required&quot; &#8211;,
&quot;PK&quot; is short for &quot;Primary Key&quot;. When you choose the
data type, you can select option <i> &lt;new data type&gt;</i> from the
combo box.  This will cause the list of available data types to be
displayed.</p>

<p>As we shall see, some entities have to be associated with other entities
to be uniquely identified.  Such entities are called <a href="#weak-entity">
weak or dependent</a>.  Other entities are 
<a href="#strong-entity">strong or independent</a>. Always start your analysis
from independent entities.</p>

<hr><h3><a name="Więzy">Integrity constraints</a></h3>

<p><i>Integrity constraints</i> of an entity are defined on tab
<i>Check</i>.  Here is an example of an integrity constraint enforcing that
an employee's salary must be higher that 1000:

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_4.png"></p>

<hr><h3><a name="Indeksy">Indexes</a></h3>

<p>Among the attributes of an entity we distinguish groups
that are used to search instances of this entity. Such a group may consists
of only one element,
For such groups of attributes we specify <i>indexes</i>.  The index for the primary key is created 
automatically and you need not create it yourself.</p>

<p><a name="idenksy-unikatowe">There are two kinds of indexes: <i>unique indexes</i>
(based on attributes that constitute <a href="#alternative-key">an alternative key</a>) 
and <i>non-unique indexes</i> (based on a set of attributes which is not a key).</p>

<p>On a diagram attributes that have unique indexes are labeled  with the letter U with subsequent 
numbers, e.g. U1, U2. Non-unique indexes are marked with the letter I with subsequent 
numbers, e.g. I1, I2.</P>

<p>In MS Visio indexes are defined on tab &quot;Indexes&quot;. Here is an example 
of the specification of a non-unique index used to search persons with a specific name:</p>

<p align="center"><img border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_15.png"></p>

<hr><h3><a name="Zwiazek">Relationship</a></h3>

<p><i>A relationship</i> is an ordered list of entities.
Some entities may be repeated on such a list.</p>

<p><a name="Kazdy">Every relationship</a> defines a certain correspondence among a set of instances of entities
taking part in a relationship.  It is <i>an instance of the relationship</i>. The relationship
can be formally written using relational notation:</p>

<p align="center"><i>Z</i>(<i>E</i><sub>1</sub>, ... , <i>E<sub>n</sub></i>)</p>

<p>That means that entities <i>E</i><sub>1</sub>, ... , <i>E<sub>n</sub></i> are related
by <i>Z</i>.</p>

<p>For example:
<table><tr><td  class="przyk">
<ul>
  <li>An <i>employee</i> works in a <i>department</i>.
  <li>An <i>employee</i> is assigned a <i>role</i> in a <i>project</i>.
  <li>A <i>country</i> exports a <i>product</i>.
</ul>
</td></tr></table>

<hr><h3><a name="Zwiazek binarny">Binary relationship</a></h3>

<p><i>A binary relationship</i> has two arguments and is rendered as a line that connects
two boxes (entities).</p>

<p>MS Visio automatically creates the attribute <i>Id</i> in the entity
<i>Person</i> (with the label
FK1).  It is <u>the foreign key</u>
that stores associations between instances of the entity <i>Person</i>
with instances of the entity <i>Department</i>.</p>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_5.png"></p>

<p><u>Warning</u>: The red squares at the ends of the line indicate 
that the entities are
connected to the relationship.  If these squares are absent, the relationship is not connected 
to entities.</P>

<p>An instance of a binary relationship is a binary relation, i.e. a finite subset of
the Cartesian product of the sets of instances of both entities. In this examples they are
the set of persons and the set of departments.</p>

<hr><h3><a name="Zw">Many-one relationship</a></h3>

<p>If the instance of a binary relationship is a partial function, such a relationship
is called <i>many-one</i>.</p>

<table><tr><td  class="przyk">
The instance of the many-one relationship between entities <i>Person</i> and 
	<i>Department</i> is a function that maps the set of <i>persons</i>
	to the set of <i>departments</i>.
</td></tr></table>

<p>The part of the relationship that corresponds to the domain of this function is called
</i>the detail entity</i>, while the entity that constitutes the
range of this function is called </i>the master entity</i> and is indicated by the arrow.</p>

<table><tr><td  class="przyk">
<i> Department</i> is the master entity; <i>Person</i> is the detail entity.
</td></tr></table>

<p>It is time for a simple task:</p>

<table><tr><td  class="notec">
<p><a href="javascript:popUp('ok1.html',350,180)">Connect</a> pairs
of corresponding terms: <i>column</i>, <i>entity</i>, 
<i>table</i>, <i>attribute</i>, <i>key</i>, <i>many-one relationship</i>,
<i>row</i>, <i>unique identifier</i>, <i> foreign key</i> and <i>instance of an entity</i>.
</td></tr></table>

<h4><a name="Implementacja">Implementation of a many-one relationship</a></h4>

<p>Two entities connected with a many-one relationship are implemented as two tables. 
The foreign key is added to the detail entity.  This foreign key stores the association with
the instance of the master entity.</p>

<table><tr><td  class="przyk">
In our example the foreign key <i>Id</i> is added (labeled with FK1) to the 
entity <i>Person</i>.
<i>Id</i> defines the link to an instance of the entity <i>Department</i> - 
<i>Id</i> stores a value taken from the primary key <i>Id</i> of <i>Department</i>.
</td></tr></table>

<p>It is time for another simple task:</p>

<table><tr><td  class="notec"><a href="javascript:popUp('ok2.html',450,130)">
Connect</a> rows of corresponding terms: <i>domain of a function</i>,
<i>one</i>, <i>master entity</i>, </i>range of a function</i>, <i>many</i> and
<i>detail entity</i>.</tr></table>

<h4><a name="Okienko">Window &quot;Database properties&quot;</a></h4>

<p><b><a name="Zakladka">Tab &quot;Definition&quot;</a></b> defines the
relationship as an association between two sets of attributes.  These sets are
the automatically created foreign key in the detail entity and 
the primary key of the master entity.</p>

<table><tr><td  class="przyk">
In our example the entity  
<i>Person</i> is the detail while the entity <i>Department</i> is the
master.
</td></tr></table>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_6.png"></p>


<p><b><a name="Zakładka &quot;Name&quot;">Tab</a> &quot;Name&quot;</b>
indicates how to read the relationship.  It also contains the name of 
the referential integrity constraint <i>Department_Person_FK1</i>.</p>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_7.png"></p>

<p><b><a name="Zakładka &#8220;Miscelaneous&#8221;">Tab </a>
&quot;Miscellaneous&quot;</b> shows the basic properties of the relationship:

<ol>
<li><a name="liczeb"><b>Cardinality</a></b> - how many instances of the
  detail entity may be associated with one instance of the master entity. It
  may be a given number (e.g. 2) or a statement like "zero-or-more",
  "one-or-more", "zero-or-one".
<li><b><a name="typzw">Relationship type</a></b>:
  <ul>
  <li><a name ="weak-entity">
	<i>Identifying</i></a> - in order to identify an instance of the detail entity
	you have to know the associated instance of the master entity.
	Such a detail entity is called <i>weak</i> (or <i>dependent</i>).
	If the relationship is identifying, the foreign key is an element of
 	the primary key of the detail entity.
  <li><a name ="strong-entity">
	<i>Non-identifying</i></a> - in order to identify an instance of the
	detail
        you need not know the associated instance of the master entity.
        Such a detail entity is called <i>strong</i> (or <i>independent</i>).
        If the relationship is non-identifying, the foreign key is not an element of
        the primary key of the detail entity.
  </ul>
<li><b><a name="opcja">Optional</b></a> - Is the value of the foreign key
optional?  Can the foreign key be NULL? The relationship is <i>optional</i>
if the value  of the foreign key can be NULL. The relationship is
<i>mandatory</i> if the value  of the foreign key must be specified and
cannot be NULL. In other words, each instance of the detail entity is
associated with exactly one instance of the master entity.
</ol>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_8.png"></p>

<table><tr><td  class="przyk">
The relationship between <i>persons</i> and <i>departments</i>
has cardinality "zero-or-more", is non-identifying and optional.
</td></tr></table>

<table><tr><td  class="przyk">
Consider the relationship between orders and line items.  It is an example of 
a relationship of cardinality "one-or-more" that is identifying and
mandatory (not optional).
Every order consists of one or more line items with ordered products. 
The order
identifies its line items (without the order there are no line items!).
Every line item belongs to exactly one order.
Entity <i>Line Item</i> of <i>Order</i> is weak (dependent).
Try to draw a diagram with customers, orders, line items and products.
Here is a possible <a href="javascript:popUp('images/orders.png',620,380)">solution</a>.
Could you give another example of an identifying relationship? 
</td></tr></table>

<p>Here is a simple question:</p>

<table><tr><td  class="notec">
<a href="javascript:popUp('ok4.html',400,200)">Can</a> you
give an example of an optional identifying relationship?</td></tr></table>

<p><b><a name="Zakadka">Tab</a> &quot;Ref. Integrity&quot;</b>
defines actions that are performed when referential integrity can be
lost as result of a deletion or an update of an instance of the master
entity.</p>

<p align="center"><img border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_9.png"></p>

<p><table><tr><td  class="notec">Here is the list of the possibilities:

<ol>
<li><i>No action</i> (<i>Restricted</i>) - restricts the change when it
	breaks the integrity constraint.
<li><i>Cascade</i> - in case of an update of the primary key of 
an instance of the master entity, updates the value of the foreign key 
accordingly in the associated instances of the detail entity.
In case of a deletion of an instance of the master entity, 
deletes also all the associated instances of the detail entity.
This option is natural of identifying relationships.
<li><i>Set Null</i> (<i>Nullify</i>) - if an instance of 
the master entity is deleted or its primary key is updated, 
sets the value of the foreign key of
the associated detail entities to NULL.
<li><i>Do not enforce</i> - allows updates and deletions of instances 
of the master entity even when they break integrity rules.
</ol></td></tr></table>

<p>Other systems as well as the standard SQL have one more option:

<p><table><tr><td  class="notec">Here is the list of the possibilities:

<ol start="5">
<li><i>Set Default</i> - if an instance of
the master entity is deleted or its primary key is updated,
sets the value of the foreign key of
the associated detail entities to the default value defined for the columns
of the foreign key..
</ol></td></tr></table>

<hr><h3><a name="Trans">Many-many relationship</a></h3>

<p>Every many-many relationship must be converted to a number of 
many-one relationships.</p> 

<table><tr><td  class="notec">
<ul>
<li>A <i>multi-argument relationship</i>, i.e. a relationship 
     with more than two arguments
	<i>Z</i>(<i>E</i><sub>1</sub>, ..., <i>E</i><sub><i>n</i></sub>) where
	<i>n</i> &gt; 2 is converted into a new entity <i>E</i><sub>0</sub>
	and <i>n</i> many-one relationships <i>Z</i><sub><i>i</i></sub>(<i>E</i><sub>0</sub>,
	<i>E</i><sub><i>i</i></sub>) that connect the new entity with the original
	entities.  The key of the entity <i>E</i><sub>0</sub> is the
	union of keys of entities <i>E</i><sub>1</sub>, ...,
	<i>E</i><sub><i>n</i></sub>.
<li>A many-many binary relationship <i>Z</i>(<i>E</i><sub>1</sub>,
	<i>E</i><sub>2</sub>) is converted into a new entity <i>E</i><sub>0</sub>
        and two many-one relationships
	<i>Z</i><sub>1</sub>(<i>E</i><sub>0</sub>, 
        <i>E</i><sub>1</sub>) and <i>Z</i><sub>2</sub>(<i>E</i><sub>0</sub>,
        <i>E</i><sub>2</sub>) that connect the new entity with the original
        entities.  The key of the entity <i>E</i><sub>0</sub> is the
        union of keys of the entities <i>E</i><sub>1</sub> and
        <i>E</i><sub>2</sub>.
</ul>

The new entity which represents the relationship 
is called an <i>associative</i>. It is alway weak (dependent), because the
many-one relationships that point to the original entities are identifying. 
</td></tr></table>

<p>Here is an example of the conversion of a three-argument relationship:</P>

<p align="center">
<table><tr><td  class="przyk">
<p>An <i>employee</i> plays a <i>role</i> in a <i> project</i>.</p>
</td></tr></table>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_10.png"></p>

<p>We applied the method described above. We introduced new associative entity, 
which represents the relationship among <i>persons</i>, <i>roles</i> and
<i>projects</i>. The key of this entity consists of the foreign keys 
of the newly created many-one relationships with entities <i>Person</i>,
<i>Role</i> and <i>Project</i>.</p>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_11.png"></p>

<ul>
<li>It is crucial to set these relationships to be identifying. Without it the foreign keys
	that reference entities <i>Person</i>, <i>Role</i> and <i>Project</i> will not be put
	into the primary key of associative entity <i>Participation</i>.
<li>Into an associative entity you can put attributes that characterize the relationship.
	For instance the entity <i>Participation</i> might have the attribute <i>Period</i>.
</ul>

<hr><h3><a name="Rek">Recursive relationship</a></h3>

<p><i>A recursive relationship</i> connects an entity with itself, e.g.</p>

<p align="center"><table><tr><td  class="przyk">
<p>A <i>person</i> <u>is the manager of</u> another <i>person</i>.
</td></tr></table>

<p>In order to define this relationship in MS Visio, we create the loop of the relationship
around the entity <i>Person</i>. Then we add a new attribute <i>Mgr</i> to this entity. 
On tab &quot;Definition&quot; we link this attribute with the primary key (<i>Empno</i>).</p>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_12.png"></p>

<p>Note that we also created indexes on foreign keys. It is the usual practice.</p>

<hr><h3><a name="Zwiazki">One-to-one relationship</a></h3>

<p>There is a special kind of many-one relationship that can have the 
implementations which
are more efficient than the standard method based 
on the foreign key and the primary key.</p> 

<p>This is the many-one relationship with instances that are partial injective functions, e.g.</p>

<p align="center"><table><tr><td  class="przyk">
<p>Every <i>student</i> <u>is</u> a <i>person</i>, but a <i>person</i> <u>need not be</u> a 
<i>student</i>.
</td></tr></table>

<p align="center"><img  border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_14.png"></p>


<h4>Methods to map one-to-one relationships onto database tables</h4>


<p>As an example we will consider the relationship between the entities
<i>Person</i> and <i>Student</i>.</p>

<table><tr><td  class="notec">
<ol>
<li>(This method is applied by MS Visio) Two tables are created:
	<i>Person</i> and <i>Student</i>. <i>Student</i> is the detail and
	is connected to the master table <i>Person</i> by the foreign key, which
	is also the primary key of <i>Student</i>.  The table <i>Student</i>
	contains also the attributes which are associated only with students.
    <ul><li>The drawback of this solution is the high cost of the joining
	of the two tables that must be often performed.
    </ul>
<li>Only one table <i>Person</i> is created.  This table stores all possible attributes
	of persons.  If a person is not a student, the student's attributes  
	are set to NULL.
    <ul><li>The drawback of this solution is the possible high number of NULL values. </ul>
<li>Only one table <i>Student</i> is created. If a new category of persons 
	is needed (e.g. <i>Employee</i>), a separate table for this category is
	created. If you need informations of all persons, you have to
	compute the union of the contents all these tables. 
    <ul><li>This method is good if the categories are disjoint.
	<li>If the categories overlap, the same information will be repeated
	(e.g. the name of a student that is also an employee will be
	stored in both tables).
    </ul>
</ol></td></tr></table>


<hr><h3><a name="Generowanie">Generating the database</a></h3>

<p>After you choose the target system (we have chosen MS Access), we can make
MS Visio generate appropriate database tables.</p>

<table><tr><td  class="notec">
<ol>
<li>Create an empty database in MS Access.
<li>In MS Visio choose the menu item "Database -&gt; Generate" (<i>Generate
	Wizard</i> will appear).
<li>On the first page choose &quot;Generate new database&quot;.
<li>If you use the wizard for the first time for this diagram:
  <ul>
  <li>Choose options &quot;Create MDB file&quot; and &quot;New&quot;
	(data source name - DSN).
  <li>On the next pages choose options  &quot;System data source&quot; and
	 &quot;Microsoft Access driver&quot;.
  <li>After you have created DSN, type the path to the Access database created
	previously.
  </ul>
<li>If you use the wizard not for the first time for this diagram:
  <ul>
  <li>Choose options &quot;MDB file already exists&quot;.
  <li>On the next pages choose DSN and the path to the existing database
	from the combo box.</li>
  </ul>
</li>
</ol>
</td></tr></table>

<p>After you have generated the database, you can open it and you will find 
the following:</p>

<p align="center"><img border="0" src="https://gakko.pjwstk.edu.pl/materialy/2398/lec/wyklad03/images/3_13.png"></p>

<hr><h3><a name="Przyk">Final task</a></h3>

<p>At the end please solve a simple task on drinkers.</p>

<table><tr><td  class="przyk">
Create the entity-relationship diagram for the information on
<i>drinkers</i>, <i>bars</i> and <i>beers</i>. Model the following
relationships:
 
<ol>
<li>A bar <i>serves</i> a beer.
<li>A drinker <i>likes</i> a beer.
<li>A drinker <i>frequents</i> a bar.
<li>A drinker <i>likes best</i> a beer.
<li>A brewery <i>brews</i> a beer.
</ol>

<p><a href="javascript:popUp('images/piwo.png',600,530)">Solution.</a></p>

</td></tr></table>

<hr><h3><a name="Podsumowanie">Summary</a></h3>

<p>Lecture 3 presents a method to construct the database schema by means of
an <i>entity-relationship diagram</i> for the application domain.
Entity-relationship diagram is the data model of this domain. It is much
simpler than the database schema, because it abstracts from the technical
details of the data representation in a give database system. Special
software called <i>CASE</i> (= Computer Aided System Engineering) provides
tools to design and draw diagram on the computer's display. It can also
generate automatically the schema of a database in a given database
system.</p>

<p>Entity-relationship diagram consists of components of three kinds:
<i>entities</i>, <i>attributes</i> and <i>relationships</i>. An entity is
mapped onto a relational table while an attribute becomes a column.
<i>Many-one relationships</i> have special meaning because they are
directly mapped onto the <i>foreign key-primary key</i> pair that is used 
to realize the association between the two related entities. Before the
implementation other
relationships must be converted into <i>associative entities</i> and a bunch
of many-one relationships. 
A many-one relationship may be <i>identifying</i> (the foreign key becomes a
subset of the primary key)  or <i>non-identifying</i> (the foreign key is
not a subset of the primary key).  Non-identifying relationships may be
<i>optional</i> (in this case the value of the foreign key may by NULL). 
There are also specific methods to implement <i>one-to-one
relationships</i>.</p> 


<hr><h3><a name="Slownik">Dictionary</a></h3>

<dl>

<dt><a href="#Atrybut">attribute</a>
<dd>A property of entities of a given type. It is represented as a certain
value like an integer, a real number or a string.

<dt><a href="#Zwiazek binarny">binary relationship</a>
<dd>A relationship with two arguments.  It relates two sets of entities.

<dt><a href="#liczeb">cardinality of a relationship</a>
<dd>the number of instances of the detail entity that may be associated 
with one instance of the master entity. It may a given number (e.g. 2) or a statement
like "zero-or-more", "one-or-more", "zero-or-one". 

<dt><a href="#Encja">entity</a> (object)
<dd>Something that exists and can be distinguished from other beings and
the information about an entity must be known or stored. Entities with the
same properties constitute types (sets) of entities. The graphical
representation of an entity is a rectangular frame.

<dt><a href="#weak-entity">identifying relationship</a>
<dd>A many-one relationship implemented by the foreign key that is a subset
	of the primary key.

<dt><a href="#Kazdy">instance of a relationship</a>
<dd>A relation among sets of instances of the entities that participate in a
relationship.  Usually it changes in time. 

<dt><a href="#Klucz">key</a> (unique identifier)
<dd>A set (may be a singleton) of attributes of the same entity such that
their values identify every instance of this entity. An entity
can have any number of keys. One of these keys is designated to be
<i>primary</i> while the others are <i>alternative</i>.

<dt><a href="#opcja">mandatory relationship</a>
<dd>A many-one relationship implemented by the foreign key that must not
        be assigned the NULL value.

<dt><a href="#Zw">many-one relationship</a>
<dd>A binary relationship whose instances are partial functions.

<dt><a href="#strong-entity">non-identifying relationship</a>
<dd>A many-one relationship implemented by the foreign key that is not a subset
        of the primary key.

<dt><a href="#Zwiazki">one-to-one relationship</a>
<dd>A binary relationship whose instances are partial injective functions.

<dt><a href="#opcja">optional relationship</a>
<dd>A non-identifying relationship implemented by the foreign key which may
	be assigned the NULL value.

<dt><a href="#Rek">recursive relationship</a>
<dd>A binary relationship that connects the same entity playing two
different roles.

<dt><a href="#Zwiazek">relationship</a>
<dd>An ordered list of entities. Some entities may be repeated on such a list.
 
</dl>

<hr><h3><a name="Zadania">Exercises</a></h3>

<h4><a name="Zadanie 1">Exercise 1</a></h3>

<p>Draw the entity-relationship diagram for a LIBRARY with information on
<u>books</u> (i.e. title, original title, publication year,
edition, language, original language, value), <u>subjects/domains</u> of
books, <u>authors</u> and <u>translators</u> (first name, second name,
language), <u>publishers</u> (name, city, zip code, address, e-mail, phone),
<u>copies</u> of books available in the library (signature), <u>readers</u>
(first name, second name, SSN, address, phone), <u>hires</u> (hire date and
return date).</p>

<ol>
<li><p>Start Microsoft Visio 2000.  Choose the type of the diagram:
	&quot;Database Model Diagram&quot;.
Objects on the diagram are created by dragging the icons from the left frame on the screen
(two groups are important: &quot;Entity Relationship&quot; i &quot;Object Relational&quot;).
If you want to access the database properties of objects of the data model, simply
double-click the object or &quot;Database properties&quot; choose the pop-up menu that
appears after you right-click the object. </p>

<p>When you create an entity, you set its 
attributes.  In tab "Columns" use physical data types of MS Access
("Physical Data Type"). Type names of subsequent columns and set the "Req'd" check box
for mandatory attributes.  Define the type for each column.  The default data type is 
<code>CHAR(10)</code>.  If you want to change it, click button "Edit..." and choose
tab "Data Type" in the pop-up window "Column properties for...". On this tab
choose Microsoft Access from the list of installed drivers (unless it has already been set
as default in the menu item "Database -&gt; Options -&gt; Drivers") and click "Change".  In the next window
choose "Native Type" from the combo box and set the size of the data type.</p>

<p>To join two entities with a relationship, drag the icon "Relations" 
and connect two ends
with the selected entities.  After you connect a relationship with an entity, you should
see a red square.  To open the window with properties of the relationship, select
it and
double-click. Fill in four tabs "Definition", "Name",
"Miscellaneous" and "Ref. Integrity". It was presented before in part 
<a href="#Okienko" target="_blank">Window "Database properties"</a>.</p>


<li>Identify all required entities in the database for a library together with their attributes.
Give short textual definitions of each entity (tab "Notes").

<li>For each entity choose the attributes of the primary key (PK).  Their values 
should uniquely identify instances of the entity.  These attributes will appear 
in the upper section of the frame of the entity.  Do not define attributes for foreign keys.
These will be created automatically by MS Visio. When you connect entities to 
a relationship MS Visio adds copies of the attributes of the primary key of the master
entity to the set of the attributes of the detail entity.  Carefully choose the primary key
for the entity <i>Hire</i>.  Give short textual definitions of the attributes
(after you choose a column, use the tab "Notes").

<li><p>Design relationships among entities.  They should cover the following facts:</p>

<ul>
<li>Every book has one or more authors; every author wrote at least one book
	(this is a many-many relationship!).
<li>Every book was published by exactly one publisher, but a publisher may publish
	many books.
<li>The identifier of each copy of a book indicates the title of the book.
<li>Entity <i>Hire</i> should contain the information who and what hires.
</ul>

<p>What kind of relationships are you going to use (identifying or non-identifying)?</p>

<li>Take a look at the obtained entity-relationship diagram. For each relationship
open its property window. In tab "Name" set two names of the relationship
in fields "Verb Phrase" (read from the detail to the master) i "Inverse Phrase"
(read from the master to the detail).  Give a short textual definition (use tab "Notes").
Set the cardinality, the kind (Identifying or Non-identifying) and the optionality
(check box "Optional").  Establish referential actions on tab "Ref. Integrity" 
for the deletion and the update of instances of the master entity:
frames "On parent delete" and "On parent update" 
(<a href="#Zakadka" target="_blank">refer to the lecture for details</a>).

<LI>The entity-relationship is now ready and we can generate an empty database as
described in the lecture in section <a href="#Generowanie" target="_blank">Generating the database</a>.
MS Visio allows to create databases for different environments.  The only requirement is to define
DSN.
</OL>


<h4><a name="Zadanie 3">Exercise 2</a></h4>
<p>Draw the entity-relationship diagram for your database application.</p>
