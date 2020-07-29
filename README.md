# The Internals #8 - Looking inside the JavaScript Specification

## Recording
[https://youtu.be/uOPeWRiIiK0](https://youtu.be/uOPeWRiIiK0)

## Resources from the discussion

### What is Ecmascript specification? 
Spec link - https://tc39.es/ecma262

Built by TC39 delegates
4 stage process - https://tc39.es/process-document/


### Engine262 - let's look at a JavaScript engine, written in js itself.
- engine262/engine262: An implementation of ECMA-262 in JavaScript
- Basic setup, host environment, run if-else. 

### How does If else work internally? 
- https://tc39.es/ecma262/#sec-if-statement-runtime-semantics-evaluation - Ifstatement.mjs - Line 24


### Completion records - Every statement and expression in Javascript internally return a completion record. What are those?
 - (#sec-completion-record-specification-type)
 - Statements.. return something? Example with eval. Do expression proposal.

### What happens when you declare a function (function declaration vs function expression)? 
	Declarations - #sec-function-definitions-runtime-semantics-instantiatefunctionobject - InstantiateFunctionObject.js Line 24
	Expressions - #sec-function-definitions-runtime-semantics-evaluation - NamedEvaluation.mjs Line 37, Line 55 (arrow)
	OrdinaryFunctionCreate - function-operations.mjs Line 201
	OrdinaryCallBindThis - #sec-ordinarycallbindthis - function-operations.mjs Line 79
	FunctionDeclarationInstantiation - #sec-functiondeclarationinstantiation - EvaluateBody.mjs Line 73
	Arguments - #sec-createmappedargumentsobject - arguments-operations.mjs Line 187

### How are arrow functions and normal functions different internally? 
thisMode - can be “lexical”, “strict” or “global”
(#sec-ecmascript-function-objects)

### What happens when a function is called? How are "arguments" and "this" available magically? 
- this - Sets envRec.[[ThisValue]]
- Let's run this in engine262. 

### Arrays 
- How are arrays different from normal objects? 
[[DefineOwnProperty]] - array-objects.js Line 34
- What happens when you set the value of a array index, or the "length" ? 
#sec-arraysetlength -  array-objects.js Line 129
- Array exotic objects - #sec-array-exotic-objects
#sec-ordinarydelete
-How is an array created using array literals (like [10, 20, , ...someArr]) ? 
#sec-runtime-semantics-arrayaccumulation - ArrayLiteral.mjs Line 45
- How does in-built Array iterator work? 
#sec-%arrayiteratorprototype%.next - ArrayIteratorPrototype.mjs Line 20
- How does array destructuring work then? - like [a, b, ...c] = someArr. 
- Let's look at some array methods - arr.entries()
.forEach (vs for..of)
.concat
.reduce
#sec-array.prototype.foreach - ArrayPrototypeShared.mjs Line 203
- Let's run this in engine262.

## Other Resources
### Guide 

- [How to Read the ECMAScript Specification](https://timothygu.me/es-howto/) (- By Timothy Gu)
- [Understanding the ECMAScript spec, part 1](https://v8.dev/blog/understanding-ecmascript-part-1) (V8 series)
- [How to read Ecmascript specification?](https://www.youtube.com/watch?v=1OLiwuOeVUY) (By Abhas Bhattacharya)

### Ask / discuss -
IRC on freenode - [#tc39](https://www.irccloud.com/invite?channel=%23tc39&hostname=irc.freenode.net&port=6667)
Discourse - [https://es.discourse.group/](https://es.discourse.group/)

### Podcast / Streams - 
- [TC39er podcast](https://tc39er.us/)
- [Compiler compiler by Yulia Startsev](https://www.twitch.tv/codehag)
- [TC39 panel discussions on Youtube](https://www.youtube.com/results?search_query=tc39+panel&page=&utm_source=opensearch)

### Misc
- [Outreach committee](https://github.com/js-outreach/js-outreach-groups)
- TC39 [meeting notes](https://github.com/tc39/notes/tree/master/meetings) and issues - to find decision logs
- TC39 website - [(tc39.es)](tc39.es)
- Spec link - [https://tc39.es/ecma262](https://tc39.es/ecma262)
