# From Command Line #

If you are using the standalone jar distribution of Erca, here is what you should do.

The main command is:

```
java -jar erca_<version number>.jar
```

Arguments for this command are:

### Using RCA ###

**clfdot** **_src_** **_tgt_**
  * **_src_**: path to the file containing the concept lattice family (in XMI),
  * **_tgt_**: path where to put the generated dot code.

Description: generates a dot file in **_tgt_** corresponding to the given **_src_** concept lattice family.

Example:
```
java -jar erca_<version number>.jar clfdot test.clf.xmi test.clf.dot
```

**clfbuild** **_--rcft src xmi tgt_**
  * **_src_**: path to the relational context family file in RCFT format,
  * **_xmi_**: path where to store the XMI of the context family generated from the RCFT,
  * **_tgt_**: path where to store the XMI of the computed concept lattice family.

Description: generate the XMI (xmi) and the concept lattice family (tgt) corresponding to the given relational context family (src) in the rcft format.

Example:
```
java -jar erca_<version number>.jar clfbuild --rcft test.rcft test.rcf.xmi test.clf.xmi
```

**clfbuild _--xmi src tgt_**
  * **_src_**: path to the file containing the relational context family in XMI,
  * **_tgt_**: path where to store the XMI of the computed concept lattice family.

Description: generate the concept lattice family (tgt) corresponding to the given relational context family in the xmi format (src).

Example:
```
java -jar erca_<version number>.jar clfbuild --xmi test.rcf.xmi test.clf.xmi
```

**rcfhtml _--rcft src tgt_**
  * **_src_**: path to the relational context family file in the RCFT format,
  * **_tgt_**: path where to store the generated HTML.

Description: generate the HTML code (tgt) corresponding to the given relational context family (src) in the rcft format.

Example:
```
java -jar erca_<version number>.jar rcfhtml --rcft test.rcft test.rcf.html
```

**rcfhtml _--xmi src tgt_**
  * **_src_**: path to the relational context family file in the XMI format,
  * **_tgt_**: path where to store the generated HTML.

Description: generate the HTML code (tgt) corresponding to the given relational context family (src) in the xmi format.

Example:
```
java -jar erca_<version number>.jar rcfhtml --xmi test.rcf.xmi test.rcf.html
```


### Using FCA ###

**latdot _src tgt_**
  * **_src_**: path to the lattice file in the XMI format,
  * **_tgt_**: path where to store the generated dot code.

Description: Generate a dot file in tgt corresponding to the given (src) concept lattice.
Example:
```
java -jar erca_<version number>.jar latdot test.lat.xmi test.lat.dot
```


**latbuild _--csv src xmi tgt_**
  * **_src_**: path to the formal context file in CSV format,
  * **_xmi_**: path where to store the XMI of the formal context generated from the CSV,
  * **_tgt_**: path where to store the XMI of the computed concept lattice.

Description: Generate the XMI (xmi) and the concept lattice (tgt) corresponding to the given formal context (src) in the csv format.

Example:
```
java -jar erca_<version number>.jar latbuild --csv test.csv test.fc.xmi test.lat.xmi
```

**latbuild _--xmi src tgt_**
  * **_src_**: path to the formal context file in XMI format,
  * **_tgt_**: path where to store the XMI of the computed concept lattice.

Description: Generate the concept lattice (tgt) corresponding to the given formalcontext (src) in the xmi format.

Example:
```
java -jar erca_<version number>.jar latbuild --xmi test.fc.xmi test.lat.xmi
```


### Graphical User Interface ###
**gui**

Description: Launch the graphical user interface to edit a relational context family (**highly experimental, use at your own risk**)

Example:
```
java -jar erca_<version number>.jar gui
```

# From Java #

## Creates a concept lattice from a formal context ##

```
ConceptLatticeGenerator clg = new ConceptLatticeGenerator(formalContext);
clg.generateLattice();
```