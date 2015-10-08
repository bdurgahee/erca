# By Hand #

Erca come with a dedicated syntax to define formal contexts seamlessly. In fact there are three different syntaxes: two for the formal contexts and one for the relational context families. Let's start first with the formal contexts.

## Formal Contexts ##

There are two available formats to describe formal contexts for Erca. The two following section describe these formats.

### CSV ###

This format has been developed to simplify the creation of contexts. In order to make the use of external tools possible, we choose the well known Coma Separated Values format. This way, you can create your context using [OpenOffice.org](http://www.openoffice.org) or other compatible applications. This format is very simple, the only thing to remind is to use **_,_** as separator and **_"_** as a value delimiter.

Example:

```
,"jungle","water","forest","fish","plant","mamal"
"lion","x",,,,,"x"
"carp",,"x",,"x",,
"dolphin",,"x",,,,"x"
"bear",,,"x",,,"x"
"zebra","x",,,,,"x"
"pine",,,"x",,"x",
```

### CTX ###

This format has been developed to allow a clean visualization of context file without the use of any external tools. It is somehow similar to the CSV format, but uses **_|_** as a separator.

Example:

```
|		| jungle	| water		| forest	| fish		| plant		| mamal		|
| lion		| x		|		|		|		|		| x		|
| carp		|		| x		|		| x		|		|		|
| dolphin	|		| x		|		|		|		| x		|
| bear		|		| 		| x		|		|		| x		|
| zebra		| x		|		|		|		|		| x		|
| pine		|		|		| x		|		| x		|		|
```

## Relational Contexts ##

### RCFT ###

This format is an extension of the Ctx format. It has been designed to design relational context families. The main differences between Rcft and Ctx is that in Rcft you can define either formal or relational contexts. When defining a relational context, you have to specify which is the source formal context and which is the target formal context.

Example:

```
FormalContext class
|       | name:BA	| name:TA     | name:BAH         |name:TC         |
| BA    | x      	|             |                  |                |
| TA    |        	| x           |                  |                |
| BAH   |        	|             | x                |                |
| TC    |        	|             |                  | x              |


FormalContext property
|       | name: balance   | name:lstBA      | name:lstTA     |
| bBA   | x               |                 |                |
| bTA   | x               |                 |                |      
| lstBA |                 | x               |                |               
| lstTA |                 |                 | x              |

RelationalContext owns
source class
target property
scaling com.googlecode.erca.framework.algo.scaling.Wide
|               | bBA         | bTA         | lstBA            | lstTA          |
| BA            | x           |             |                  |                |
| TA            |             | x           |                  |                |
| BAH           |             |             | x                |                |
| TC            |             |             |                  | x              |


RelationalContext type
source property
target class
scaling com.googlecode.erca.framework.algo.scaling.Wide
|       | BA          | TA         | BAH       | TC         |
| bBA   |             |            |           |            |
| bTA   |             |            |           |            |
| lstBA | x           |            |           |            |
| lstTA |             | x          |           |            |
```

# From Java #

Erca also come with a Java API that allows you to instantiate, manipulate and serialize Formal and Relational Contexts. You can consult the ErcaMetamodel to see the class hierarchy of our metamodel for Formal/Relational Concept Analysis. The following sections show little snippet that indicates how to instantiate formal and relational contexts.

## Formal Contexts ##

```
// Creates a formal context
FormalContext fc = RcfFactory.eINSTANCE.createFormalContext();

// Creates an entity.
Entity ent = ErcaFactory.eINSTANCE.createEntity();
ent.setName("Lion");

// Creates a binary attribute.
BinaryAttribute attr = ErcaFactory.eINSTANCE.createBinaryAttribute();
attr.setName("mamal");

// Adds the entity and the attribute in the context.
fc.getEntities().add(ent);
fc.getAttributes().add(attr);

// Adds a pair in the relation defined by the formal context.
fc.addPair(ent,attr);
```

## Relational Contexts ##

```
// Creates a relational context family.
RelationalContextFamily rcf = RcfFactory.eINSTANCE.createRelationalContextFamily();

// Creates two formal contexts.
FormalContext fc1 = RcfFactory.eINSTANCE.createFormalContext();
FormalContext fc2 = RcfFactory.eINSTANCE.createFormalContext();
rcf.getFormalContexts().add(fc1);
rcf.getFormalContexts().add(fc2);

// Creates a relational context.
RelationalContext rc = RcfFactory.eINSTANCE.createRelationalContext();
rc.setSourceContext(fc1);
rc.setTargetContext(fc2);
rcf.getRelationalContexts().add(rc);
```