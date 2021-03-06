## sato_tate_groups

| | |
|---|---|
|**Description**|Sato-Tate groups|
|**Status**|[production](http://www.lmfdb.org/SatoTateGroup)|
|**Contact**|[Andrew Sutherland](https://github.com/AndrewVSutherland)|
|**Code**|[sato_tate_groups](https://github.com/LMFDB/lmfdb/tree/master/lmfdb/sato_tate_groups/)|
|**Collections**|[st_groups](http://www.lmfdb.org/api/sato_tate_groups/st_groups), [st0_groups](http://www.lmfdb.org/api/sato_tate_groups/st_groups), [small_groups](http://www.lmfdb.org/api/sato_tate_groups/small_groups)|

**Todo**:
* add rational weight 0 groups of low degree (to support Artin L-functions)
* add generators for weight 1 degree 4 groups

## Collection: **st_groups**

Description: Main collection for Sato-Tate groups

Origin: Code by Andrew Sutherland

Extent: All Sato-Tate groups that arise for elliptic curves (3) and genus 2 curves (52) over a number field.  This addresses all self-dual motives with rational coefficients of weight 1 and degree up to 4.  Sato-Tate groups of weight 0 and degree 1 (not necessarily rational) are computed on the fly and not stored in the database.

### **Attributes**
 * **_id**: ObjectId generated by Mongo DB (includes creation timestamp)
 <p>**Example**:ObjectId('572bbe5bf9ae3228154a72bd')</p>
 * **component_group**:encoded as GAP id string '_a_._b_', where _a_ and _b_ are integers; _a_ is the order of the group and _b_ distinguishes groups of the same order.
 <p>**Example**: u'6.2'</p>
 * **components**: number of components (equal to _a_ in the GAP id of the component group), stored as an integer.
 <p>**Example**: int(6)</p>
 * **counts**: list of pairs [*name*,*value_list*], where *x* is a class function (*a_n* denotes the nth elementary
 symmetric function of the eigenvalues and *s_n* denotes the nth power sum), and *value_list* is a list of
 pairs [_v_,_n_] where _v_ is an integer value and _n_ is the number of components for which _x_=_v_.
 <p>**Example**: [[u'a_1',[[0,9]]],[u'a_2',[[-1,,2],[2,1]]].</p>
 * **degree**: degree of the Sato-Tate group (cohomological dimension), a positive integer
 <p>**Example**: int(4)</p>
 * **gens**: generators, stored as a list of *d*-by-*d* matrices whose entries are strings, where *d* is the degree;
 together with the identity component, they generate the group.
 <p>**Example**: [[[u'0', u'1'], [u'1', u'0']]]
 * **identity_component**: label of the identity component (string).
 <p>**Example**: 'USp(4)'</p>
 * **label**: label of the form *wt*.*deg*.*dim*.*a.bc* (string) where *wt* is the weight, *deg* is the degree,
 *dim* is the real dimension, *a.b* is the GAP id of the component group, and *c* is a letter or string of letters
 used to break ties; uniquely identifies the Sato-Tate group.
 <p>**Example**: u'1.4.10.1.1a'
 * **moments**: list of lists [*x*,*m_1*, *m_2*,..., ], where *x* is a class function (elementary symmetric or power
 sum function of eigenvalues), and *m_n* is the *n*th moment of *x*, stored as s string.
 <p>**Example**: [[u'a_1',u'1',u'0',u'1',u'0',u'3',u'0',u'14',....,u'4719'],[u'a_2',u'1',u'1',u'2',u'4',u'10',...,u'223412']]
 * **name**: string naming the Sato-Tate group unique within its weight and degree
 <p>**Example**: u'USp(4)'</p>
 * **pretty**: pretty-print version of name in latex math mode
 <p>**Example**: u'\\mathrm{USp}(4)'</p>
* **rational**: boolean indicating whether the Sato-Tate group satisfies the rationality axiom (currently always True)
<p>**Example**: bool(True)
 * **subgroups**: list of labels of maximal proper subgroups
 <p>**Example**: [u'1.4.3.1.1a']
 * **supgroups**: list of labels of minimal proper super group
 <p>**Example**: [u'1.4.3.1.1a', u'1.4.3.4.2a',u'1.4.3.6.2a']
 * **trace_histogram**: b64 encoded .png file containing 220x124 trace histogram plot.
 <p>**Example**: u'data:image/png:base64,iVBORw0KGg...II%3D
 * **trace_zero_density**: proportion of components on which the trace is identically zero, rational number encoded as a string.
 <p>**Example**: u'1/2'
 * **weight**: weight of the Sato-Tate group (nonnegative integer)
 <p>**Example**: int(1)

### Indexes
* {'**_id**':1} (created by mongo db)
* {'**label**':1} (for searching by label)
* {'**name**':1}: (for searching by name)
* {'**weight**':1}: (for browsing/searching by weight)
* {'**degree**':1} (for browsing/searching by degree)
* {'**weight**':1,'**degree**':1,'**real_dimension**':1,'**components**':1} (used to sort search results)

## Collection: **st0_groups**

Description: Collection containing information about the identity components of Sato-Tate groups

Origin: Code by Andrew Sutherland

Extent: Sato-Tate groups that arise for elliptic curves (3) and genus 2 curves (52) over any number field.  This addresses all self-dual motives with rational coefficients of weight 1 and degree up to 4.

### **Attributes**
 
* **label**: label of the identity component, currently of the form w.d.r, where w is the weight, d is the degree, and r is the real dimension (this is sufficient to uniquely identify the identity component for w=1 and d=0,2,4) but in other cases more information will be required (so the label format may need to vary with w and d).
<p>**Example**: u'1.4.6'
* **name**: text name of the identity component, used for displaying in scrolled input boxes where latex is not supported
<p>**Example**: u'SU(2)xSU(2)'
* **pretty**: pretty-print version of the name in latex math mode
<p>**Example**: u'\\mathrm{SU}(2)\\times\\mathrm{SU}(2)'
* **weight**: weight of the corresponding Sato-Tate group (nonnegative integer)
 <p>**Example**: int(1)
* **degree**: degree of the corresponding Sato-Tate group (positive integer)
 <p>**Example**: int(4)</p>
* **real_dimension**: dimension of the identity component as a connected compact real Lie group (positive integer)
<p>**Example**: int(6)</p>
* **description**: mathematical description of the identity component as a set of d-by-d matrices (latex math mode string)
<p>**Example**: u'\\left\\{\\begin{bmatrix}A&0\\\\0&B\\end{bmatrix}: A,B\\in\\mathrm{SU}(2)\\right\\}'

### **Indexes**

* {'**_id**':1} (created by mongo db)
* {'**label**':1} (for searching by label)
* {'**name**':1}: (for searching by name)
* {'**weight**':1}: (for browsing/searching by weight)
* {'**degree**':1} (for browsing/searching by degree)

## Collection: **small_groups**

Description: Collection containing information about finite groups of small order used to describe component groups of Sato-Tate groups (could also be used in many other places).

Origin: GAP

Extent: All groups of order up to 255 (up to isomorphism).  Easy to add more (up to order 1024).

### **Attributes**
 
* **label**: GAP ID encoded as a string u'N.n', where N is the order of the group and n distinguishes groups of the same order (as determined in GAP).
<p>**Example**: u'24.13'
* **name**: text discription of the group
<p>**Example**: u'C_2*A_4'
* **pretty**: pretty-print version of the name in latex math mode
<p>**Example**: u'C_2\\times A_4'
* **order**: order of the group (positive integer)
 <p>**Example**: int(24)
* **cyclic**: true if the group is cyclic, false otherwise
 <p>**Example**: bool(False)</p>
* **abelian**: true if the group is abelian, false otherwise
 <p>**Example**: bool(False)</p>
* **perfect**: true if the group is perfect, false otherwise
 <p>**Example**: bool(False)</p>
* **simple**: true if the group is simple, false otherwise
 <p>**Example**: bool(False)</p>
* **solvable**: true if the group is solvable, false otherwise
 <p>**Example**: bool(True)</p>

### **Indexes**

* {'**_id**':1} (created by mongo db)
* {'**label**':1} (for searching by label)
* {'**name**':1}: (for searching by name)
* {'**order**':1}: (for browsing/searching by order)

