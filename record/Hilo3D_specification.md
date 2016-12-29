<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline3">1. class member define order</a>
<ul>
<li><a href="#orgheadline1">1.1. common member order</a></li>
<li><a href="#orgheadline2">1.2. special member order</a></li>
</ul>
</li>
<li><a href="#orgheadline15">2. naming</a>
<ul>
<li><a href="#orgheadline4">2.1. class</a></li>
<li><a href="#orgheadline5">2.2. interface</a></li>
<li><a href="#orgheadline6">2.3. enum</a></li>
<li><a href="#orgheadline7">2.4. folder</a></li>
<li><a href="#orgheadline8">2.5. variable</a></li>
<li><a href="#orgheadline11">2.6. const</a>
<ul>
<li><a href="#orgheadline9">2.6.1. all upper case</a></li>
<li><a href="#orgheadline10">2.6.2. can use "_" naming</a></li>
</ul>
</li>
<li><a href="#orgheadline14">2.7. test</a>
<ul>
<li><a href="#orgheadline12">2.7.1. run test(.html page)</a></li>
<li><a href="#orgheadline13">2.7.2. test script with jasmine</a></li>
</ul>
</li>
</ul>
</li>
</ul>
</div>
</div>

# class member define order<a id="orgheadline3"></a>

## common member order<a id="orgheadline1"></a>

static attribute
static method

constructor

public getter->setter
protected getter->setter
private getter->setter

public attribute
protected attribute
private attribute

public method
protected method
private method

## special member order<a id="orgheadline2"></a>

abstract
virtual
common member

# naming<a id="orgheadline15"></a>

## class<a id="orgheadline4"></a>

use Pascal naming.
e.g. 
FirstClass

## interface<a id="orgheadline5"></a>

start with "I".
e.g.
IParseData

## enum<a id="orgheadline6"></a>

start with "E".
e.g.
EVariableData

## folder<a id="orgheadline7"></a>

use camel-case naming or "\_" naming.
e.g.
firstFolder
first<sub>folder</sub>

## variable<a id="orgheadline8"></a>

use camel-case naming.
e.g.
firstVariable

## const<a id="orgheadline11"></a>

### all upper case<a id="orgheadline9"></a>

e.g.
const NAME = "aaa";

### can use "\_" naming<a id="orgheadline10"></a>

e.g.
const PLUGIN<sub>NAME</sub> = "aaa";

## test<a id="orgheadline14"></a>

### run test(.html page)<a id="orgheadline12"></a>

end with "ForRunTest".
e.g.
sampleForRunTest.html

### test script with jasmine<a id="orgheadline13"></a>

end with "Spec".
e.g.
testSpec.js