# meta-lang-examples

Discuss: https://social.metaproject.frl/Meta/

# Meta **αpε**
`looper.com` & `writer.com` are αcτµαlly pδrταblε εxεcµταblε https://justine.lol/ape.html

In other words Meta compiles to an **αpε**

`writer` supports terminal pasting. Using Terminology I can paste any amount of text and save it with no issues.

```
Meta [
	title: "Meta Line Writer"
	file: ./writer.meta
]
exit: false

filename: ask/line "Save As: "
folder: "./"
extension: ".txt"
line-number: 1
word-count: 0

file-saved: to file! join/with
	             join/with folder filename extension

file-handle= try open/new file-saved

until exit [
	write line-number
	line: ask/line "> "
	if line = "eof" [close file-handle
		                exit: true
		                bye
	]
	append/line file-handle line
	increment line-number
	line-left: line
	while line-left [
	        line-left: find line " "
	        a-word: (count line) - (count line-left)
	        increment word-count
	        line: skip line a-word + 1
	]
	write join/with join/with "wc " to string! word-count " | "
	word-count: 0
]
```

```
Meta [
	title: "More Examples"
        purpose: {Original Code from:
             https://arnoldvanhofwegen.com/the/unofficial/meta/examples.html }
	file: ./looper.meta
]
forever [
        x: ask/line "> "
	if x = "" [bye]
	;comments
        ;chars: count x
	;write x write/line " =Input" 
	;write chars write/line " characters"

	if x = "help" [write "Commands: " write/line "calc help caps game board"]

	if x = "calc" [
		result: 1
		n: 4
		while n > 1 [
    			result: result * n
			write/line result 
    			decrement n
		]
	]

	if x = "caps" [
	string: (ask/line "CAPITALIZE: ")
	lower-characters: "abcdefghijklmnopqrstuvwxyz"
	upper-characters: "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
	upper-string: ""
	lower-string: ""
	length: count string
	for index [1 length][
    		lowchar: upchar: copy cut at string index 1
    		either found: find lower-characters lowchar [
        			upchar: copy cut at upper-characters (27 - (count found)) 1
    		][
			if found: find upper-characters upchar [
            				lowchar: copy cut at lower-characters (27 - (count found)) 1
        		    ]
    		]
    		upper-string: join/with upper-string upchar
    		lower-string: join/with lower-string lowchar
	]
		write/line upper-string
	]

	if x = "game" [
		write/line "Welcome to the Game of Nim."
		tokens: to whole! ask/line "Tokens? "
		write "We begin with " write tokens
		
		write/line " tokens. On each turn, a player"
		write/line "may take between 1 and 3 tokens. The player who takes the"
		write/line "last token wins."
		write/line ""

		while tokens > 0 [
    			write "Available tokens: " write/line tokens
    			; provide a visual display
    			for index [1 tokens][
        				write "⛀ ";
    			]
    			write new-line
    			answer: ask/line "How many tokens do you want to take (1, 2 or 3)?"
    			write/line ""
    			removed: to whole! answer
    			write "You have taken " write removed write/line " token(s)"

    			tokens: tokens - removed
    			computertakes: modulo tokens 4
    			write "Computer takes " write computertakes write/line " token(s)"
    			tokens: tokens - computertakes
		]
		wait 1
		write/line "No more tokens left! I took the last one! I won!"
		wait 1
		write/line "Thank you for playing! Let's play again!"
	]

	if x = "board" [
		BOARD-SIZE= 50
		Let [board] binary! BOARD-SIZE

		For index [1 BOARD-SIZE][
		    poke board index 0
		]

		for index [1 20][
		    poke board index 3
		    poke board (index + 30) 2
		]

		poke board 3 5
		poke board 48 4

		write/line ""
		for row [1 10][
   			write either is-odd row ["  "][""]
    			for line [1 5][
        				field: pick board (row - 1 * 5 + line)
        				either 0 = field [
            					write "▨"
        				][
            					either 2 = field [
                						write "⛀"
            					][
                						either 3 = field [
                    							write "⛂"
                						][
                    							either 4 = field [
                        								write "⛁"
                    							][
                        								write "⛃"
                    							]
                						]
            					]
        				]
        				write "   "
    			]
    			write/line ""
		]
		write/line ""
		]


]	
```
Plus they are extremely tiny!

```
:~$  ps aux | awk '{ print $5" "$6" "$11 }' | sort -nr

3164 2048 /usr/sbin/mcelog
2540 1792 fusermount3
528 128 ./looper
356 0 ./writer
VSZ RSS COMMAND
```

## Get Compiler Client

Check out the console: https://console.metaproject.frl/

The compiler client is currently available for web browsers, Windows, Apple MacOS, Linux, FreeBSD, NetBSD and OpenBSD.

The compiler currently produces programs for web browsers, PC platforms and for Atari 8-bit home computers. Stay tuned for more.

Download:
`https://language.metaproject.frl/programs/platforms/APE/64-bit/AMD/GCC/portable/command-line/Meta/remote/compiler/run.com`

*nix:

`chmod +x run.com ; mv run.com metacc` *Do the equivalent in Windows.*

`./metacc writer.meta`

Outputs executable: `program.com`

# Meta

Meta is being created by Kaj de Vos, with help from its community. The following are his words:

https://language.metaproject.frl

https://arnoldvanhofwegen.com/the/unofficial/meta/word/Meta.html

Meta is for people with an open mind who want to make an effort to improve. You also need to be able to handle the fact that Meta is a work in progress. It's good, but not perfect. Everyone will find in our projects what they are looking for. If you come to them with a preconception that they can't be any good, or that they should be the same as other products, your brain will trick you into interpreting everything we say negatively and you will imagine to have confirmed your preconceptions. Something can't be an improvement or innovative without being different. On the other hand, if you are curious and of good will and make an effort to understand what we are saying, you will find a lot to enjoy and use. You must be willing to have your thinking changed by Meta.

We aim to transcend a narrow focus on a specific audience. Meta is a project for developers who need power from their language, but also for occasional programmers who don't have the time to juggle many arcane details, and for people who want to learn programming and are looking for an easier language. It's a project for REBOL fans, but we also welcome programmers from other languages who want to expand their horizon. It's a project for Atari and Syllable enthusiasts, but also for all the other platforms. Meta is for fun and for profit. We don't believe in fundamental contradictions between these uses, and we don't want to create artificial limitations. We believe that, when embraced, these uses will reinforce each other.

We make this possible through Meta's unique combination of properties. Its human-friendly focus and high-level properties reduce the cognitive load on your brain. This brings the language within reach of beginning and occasional programmers, but also frees advanced developers to spend their energy on their application logic, instead of babysitting the language.

Meta's low-level properties and raw performance enable it to run on more diverse platforms than most other languages, and allow advanced developers to still babysit the language when they need to.

Now this does require some mutual understanding from everyone involved. We will build an inclusive community, where anyone with good intentions can feel welcome. The project materials will cater to all knowledge levels, so that people can grow through them.

Not everyone is willing to make the effort to learn to understand Meta and the principles it is based on. This is usually not because they are not capable of doing so, but because they are already used to other computer languages based on different principles. Some of them even fiercely resist the notion that Meta could be rational and useful, in spite of the more than half a century of scientific and practical history in related languages that are highly influential on many modern computer languages and systems. To understand why this happens, read these articles:

- The Backfire Effect, by The Oatmeal
- Theory of Bounded Rationality
- The Blub Paradox

Meta is outside their bounds of rationality, leading them to rationalisations that are bizarre to those who do understand Meta. While this is unfortunate, it also shows that Meta is a real innovation that pushes these bounds, towards greater rationality. If you want to give it a positive spin, it is also a clear way to outcompete them. We need to focus on those for whom Meta is within their bounded rationality, so they can achieve the results that show others the progress.

An odd consequence of this is that Meta needs a two-pronged approach of focusing on both beginning and advanced programmers. Beginning programmers haven't invested much yet in different languages, so they may as well try Meta. Advanced programmers have the insight to see that Meta solves several pervasive problems in programming, and the mental capacity to learn a different language. Of course, this also makes Meta suitable for medium-level programmers, but that is not in our hands: it depends on their mental agility. One can lead a horse to water, but one can't make it drink.

If you find yourself in the middle group, and you do want to make an effort to learn Meta, but you can't get your head around it, it is very useful to read the following essays. They are about Logo, Lisp and Scheme, but much the same fundamental principles apply to Meta. The second essay explains them in terms of different, popular programming and data languages such as XML, SQL, C and its preprocessor, C++, Java and C#:

- High School Computing: The Inside Story
- The Nature of Lisp

In spirit, Meta is a descendant of the REBOL and Logo languages, but with performance close to C. Meta is mostly inspired by REBOL. It is not meant to be compatible with REBOL, but it will eventually be quite close. However, it is not complete yet, and there are many subtle differences to optimise the language and extend its reach.

REBOL is the brain child of Carl Sassenrath, of previous fame as the chief designer of the innovative Commodore Amiga operating system, the first consumer multimedia system. REBOL was designed to enable the creation of Domain-Specific Languages (DSL's). Because REBOL DSL's use a different grammar than, but the same lexical syntax as the general-purpose main language, they are called dialects. They are executed in the REBOL interpreter. Dialects can not only contain program code, but also data formats. Because code is just a data dialect, it can be processed as data, allowing the language to manipulate its own code. REBOL inspired the creation of the popular JSON data dialect of JavaScript (The JSON Saga from 21:45). One of REBOL's hallmarks is a dialect for cross-platform definition of graphical user interfaces. In this way, programs are written in a combination of the main language and applicable DSL's. REBOL has a human-friendly syntax of great clarity and is highly productive. It has been measured to be the most expressive general-purpose language. When the general-purpose REBOL dialect is not optimal for a certain task, REBOL supports creating a special-purpose dialect that is optimal. This way, it is not needed to revert to entirely different DSL's that would cause a mismatch with the language. Creating dialects of both program code and data is so smooth, that it can be done routinely with small granularity. Programs will be built up out of dialects, allowing to approach the essential complexity of the task at hand.

In theory, REBOL's dialecting lets it adapt to all domains of programming. Unfortunately, there are other factors that put limits on the applicability of the language. While REBOL's expressiveness and minimal redundancy allow it to be tiny compared to many other languages, it is not tiny and efficient enough for cases where performance is critical. Nor is its architecture open enough for systems programming and other cases that demand efficient interfacing with external systems and libraries. This is due to REBOL's monolithic interpreted execution model, which makes it a relatively slow language, and due to its high-level type system, which makes it memory-hungry and does not support the data types of external systems.

Meta is close to REBOL, but solves its weaknesses. It is designed and optimised for compilation. The compiler is currently written in REBOL 3. The architecture is broadly modelled after the design of LLVM, constructed around an Intermediate Representation. The user-facing front-end language is a REBOL dialect. Its type system is a combination of the high-level type system of REBOL and a safe form of the type systems of medium-level languages such as C and Pascal. The back-end architecture was designed around WebAssembly and extended for generating C and native binary machine code. Multiple back-ends can generate and optimise code for a wide range of target platforms and target languages.

## Why?

Why make the effort to learn a new language? Software development is the process of translating human ideas and goals into instructions that a computer can execute. This is typically done in multiple steps that result in multiple layers of software, each layer a step closer to the machine and larger than the previous layer, because it is more detailed. We describe the design and specification of the software in human language. When the instructions for the machine are closer to the human language specification, fewer steps and layers are needed. You become more productive, and will have a competitive advantage compared to others who don't make the effort and stick with less expressive programming languages. It is also more fun and motivating.

It is known that the number of lines of program text a software developer can write per unit of time is largely independent of the programming language. Therefore, a language that can express more concepts in the same space - while still being readable - will make you more productive. The software will be smaller, less complex and of higher quality. It is known that, other factors being equal, the number of bugs in software is proportional to the number of lines of the program text and related to the complexity of the software. From security engineering, we know that Trusted Computing Bases (TCB) should be kept as small as possible to improve security and safety. The cost of software development and maintenance will be reduced. Because your brain capacity is limited, and there is also a limit to how organisations can stretch this limit by having multiple software developers work together, reducing the size and complexity of the software means that you can take on larger projects than before.

The young field of computing science has been struggling to establish a reliable software engineering discipline comparable to other fields of engineering. This struggle is not over, as any user of computer devices can attest to. Complexity does not equal sophistication. Reducing the complexity of software and its development process to improve its quality, reliability and safety is of general concern for society. The language in which stakeholders communicate should be brought closer together. A human-friendlier language for software, both program code and data, can not only bring the machine closer to the programmer, it can also bring the user who commissions the software closer to the developer. A friendlier specification language will enable more end users to collaborate on formal specifications with the developer, reducing confusion about their needs.

## Development Status

Meta has been under full-time development since June 2020, after a period of research and design that spanned several decades. Its name was revealed in August 2021 and it was first released in October of that year.

Is it useful for anything yet? Yes! Meta runs its own project and the others under the Meta Project umbrella. This website, the downloads, the web console and the custom forums are served to you by the language itself. Some example programs have been published. The remote Internet client to compile them is also written in Meta itself.

Compared to REBOL, its predecessor, Meta has REBOL's high-level syntax, but it doesn't yet have its high-level data types and its dynamic features, such as dynamic code generation and execution. These will be implemented over time. On the other hand, Meta far exceeds REBOL's performance, interoperability with other sub-systems, and ability to run on many platforms, including tiny ones.

Is Meta usable for you yet? That depends on your use case and your attitude. Meta is a work in progress that is being developed for its published target and host platforms, use cases and other sample programs. If your platform is supported and your use case is similar to the samples, you will have a good chance of success. Currently, you need to be willing to work around temporary limitations in the language and documentation.

Many of the current limitations can be worked around, and Meta will still reward you with outstanding results. The language is incomplete, but compiled programs are of production quality, blazingly fast, efficient and with few dependencies - unless you need garbage collection of memory for long-running programs.

If you need support, contact us for consulting or contract development.

## Supported Platforms

- Web Browsers   
- PC (Personal Computer / Laptop / Server)
- Smart Phones & Tablets
- Game Consoles & Handhelds 
- Embedded Systems
- Home Computers
- Mainframes

Meta is being developed on 64-bit Linux. In-house we have preliminary test programs written in Meta running on several other platforms and sub-platforms. So far, a compiler for web browsers and multiple computer platforms, and a cross compiler for Atari 8-bit home computers through the C back-end have been released. Stay tuned for more.

The Atari 2600 was one of the first game consoles. It has 128 bytes of RAM and an 8-bit processor running slightly over 1 MHz. It shows that the language is fast enough to "race the beam": to draw the television display scanline by scanline in real-time, hundreds of scanlines 50 to 60 times per second. It proves that Meta can target very small devices, can use native system features, and can run on bare hardware, without an operating system.

The Atari 8-bit was Atari's first personal/home computer system, follow-up to the Atari 2600. It is a complete platform, including an operating system, in a very compact and efficient form. It proves that Meta can achieve a high level of platform abstraction, by running cross-platform programs unchanged on anything from Atari 8-bit to 64-bit PC's.

The C back-ends use a C toolchain for the platform, to be able to target a broad range of platforms. The native back-ends generate machine code directly, without relying on a third-party toolchain, in the executable binary program format for the platform. The native back-ends reduce Muda compared to the C back-ends. They prove that Meta can be more efficient and less wasteful than C, both in the generated programs and the toolchain. On the other hand, the native back-ends require more work per platform for us to implement them, so the cross-platform C back-end is currently the most developed.

## Goals

Several of these goals have been achieved, most are in progress.

Strike a balance between science and practicality: apply good ideas from (computing) science to improve solutions to practical problems.

Increase programming productivity.

Improve software quality: its performance, portability, readability, reliability, security and maintainability.

Reduce cost and risk in developing and running software.

Enable more people to learn programming.

Reduce the cognitive load of programming on humans. Enable as much of a system as possible to fit in a single person's head.

Optimise the design for humans first, then for machines, including Artificial Intelligence. Make the machine work for the human, instead of the human for the machine. Don't make the human do work that the machine can figure out. Make human-friendly design choices.

Use the existing power of human language better than most computer languages. Optimise expressiveness and conciseness, while maintaining readability. Specify what you want done, let the language figure out how.

Simple where it can be, advanced where it needs to be. Different balance of complexity than other computer languages.

Smooth learning curve from beginners to advanced developers. The language is deep, but it should be possible to teach the basics to children.

Support constructionist learning.

Build interactive guidance into the language tools, to reduce the need for separate documentation.

Support collaboration on software development between humans and Artificial Intelligence.

Minimise software waste, by reducing redundancy and unnecessary work: reducing accidental complexity, leaving only the essential complexity. This goal enables a series of other goals:

Support the methodology of Lean Software Development.

Support a wide range of use cases, from systems programming to application development. We believe this can be done in one language if it is capable and flexible enough.

Support a wide range of platforms. Leave no soul behind. There should be no need to use some other language due to lack of availability.

Support both cross-platform programs and platform-specific programs.

Performance matters. Even though modern hardware enables inefficient software to handle many tasks, this comes with extra costs, and whole classes of performance-sensitive tasks remain out of reach. Performance doesn't matter until it does - and that can be suddenly during a project. Looking forward, Moore's law is running into its limits. Computer languages must be fast again to be competitive. There should be no need to use some other language because of performance.

Fast compilation times. Little waste of developer time.

Fast startup and execution times. Little waste of user time.

Produce small to tiny executable files. Little waste of storage space, memory, network bandwidth and startup time.

Build the language on itself, multiplying its strength and reducing redundancy.

Build the project on the language itself, multiplying its strength. The proof of the pudding is in the eating.

Build the language and the project incrementally, to conquer the dragon of their complexity. A journey of a thousand miles starts with taking the first step. The project will develop over many years; it is too big to do it in one go.

Release early, release often, to gather and incorporate feedback. The perfect is the enemy of the good.

Support actual use cases. Make the language usable for specific cases as soon as possible, for ourselves and others.

Support both open-source and closed, commercial software. You don't have to ship your source code with compiled programs.

Integrate well with existing systems. No language is an island.

Make use of existing sub-systems when this enables quick progress. Stand on the shoulders of giants.

One of the giants on whose shoulders we stand is the REBOL language. Bootstrap Meta off of REBOL by writing the first version in REBOL 3 and making use of REBOL's documentation, available program code, and support in tools such as text editors, as much as possible without compromising Meta's design.

However, limit dependencies, especially when these cause single points of failure. Don't stand on the shoulders of dwarves. Don't stand on the shoulders of angry giants. 

Don't stand on the shoulders of stupid giants. Don't stand on the shoulders of giants with attention deficit disorder.

Pick the low-hanging fruit in features and use cases, to make quick progress. Building the language on itself, this will usually bring the next rung of fruits within reach.

Everyone who uses the project should contribute something to it, in some way that suits them.

Sustain the project on a freemium model: a mix of crowd-funding, free and paid products and support services such as consulting and contract development.

Gradually open-source the base products, once the funding allows it. So far, we open-source everything that runs on your local machine.

Have fun creating Meta. It's a huge task, so we need to keep ourselves motivated to accomplish it.

Build an inclusive community, where anyone with good intentions can feel welcome, to help us achieve it.

### Road Map

Current priorities, in order. Because much depends on support from the community and funding by organisations, there is no time schedule for these developments. We can implement specific wishes when there is funding for them. In times when there is no funding, we will follow our own priorities, which usually follow the low-hanging fruit. If you need guarantees on certain features and their planning, contact us for contract work.
Done

Developed Meta into a Minimum Viable Product. This will be a base language with approximately the feature set and type system of medium-level languages such as C and Pascal in a safe form, made friendlier by a high-level REBOL-like syntax.

Developed a web download server written in Meta itself, to support the project and develop the language.

Introduced the project to the Atari 8-bit scene as a suitable grass-roots audience, to start a feedback process.

Created a project website, served by Meta.

Introduced the project to the REBOL audience, Meta's predecessor.

Developed an Internet build server and client written in Meta, for easy and continuous deployment of the language.

Launched the language as a cross compiler on PC to Atari 8-bit, a suitable combination of target and host platform to make a start.

Released the language for popular PC platforms themselves.

Released the language for web browsers, for even easier entry and coverage of more platforms.

Developed a custom forum system for the project, using Meta itself and served by Meta.

Introduced the project to the αcτµαlly pδrταblε εxεcµταblε & Cosmopolitan community, which we support as a target runtime.

Brought the project to the new Bluesky social network [Bluesky social network] .

Made the language available for ARM, mobile, embedded, mainframe, 32-bit and other alternative or older systems, through the new Blink virtual machine.

### In Progress

Incrementally improve the language, build services, documentation and program examples from the feedback of their use.

Use Meta for tasks in other projects.

Introduce the project to more audiences.

Build an inclusive community, where anyone with good intentions can feel welcome.

### Medium Term

Release Meta for many target and host platforms to grow the user base.

Create a crowd-funding system using Meta, to fund the project and let users influence priorities.

Develop paid premium products and services to sustain the business model.

### Long Term

Develop Meta further to implement REBOL's higher-level and dynamic features, and interface with external systems and libraries. Within these design and dependency constraints, there is a lot of room to let the crowd funding inspire the planning.

Gradually modularise Meta more to open up the project to outside contributions.

When Meta is capable enough, rewrite it from REBOL into itself.

Gradually open-source more of the project's program source code.

Because of its nature of making use of third-party open-source products, the server side of the product is hard to install and maintain. We will work towards a simpler version that can run independently on your local machine. This will take considerable work and time to achieve, and because of technical necessity, it will have limitations compared to the full product.

The audience chosen for early introduction are the Atari 8-bit and Atari 2600 communities, because these small machines are a good start to build on. They are easier to work for than modern platforms due to less complexity, and keep you aware of efficiency: these platforms hardly tolerate Muda. They provide meaningful results earlier: the Minimum Viable Product is smaller for a small platform.

The target platform chosen for the first release was the Atari 8-bit based on the CC65 back-end. This is a small but complete platform that can show all current features of Meta. CC65 is a standards-compliant but relatively basic C implementation, making it a good baseline for the C back-end. Code generated for CC65 is likely to work with most other C compilers and cross-platform C libraries. The Atari community is helping with Meta's development, so we want to show our appreciation.

There will always be a free version of Meta. We will build a business on top of it, by offering paid premium versions and other products built with Meta.

To grow the project, we very much want to release Meta as open source under a permissive licence, eventually. However, a number of criteria need to be met before that is prudent. The current implementation is written in REBOL. Once Meta is capable enough, we will rewrite it in itself. The REBOL version will then no longer be maintained, and open-sourcing a code base without maintaining it is futile. Further, we need to develop premium products to sustain the business model, before we can give away the core products for free. This will be a gradual process. So far, we open-source everything that runs on your local machine: the remote compiler client, the sample programs, the web console client and the forum client web application. As we develop more products, more of the base products can be open-sourced. We will also gradually open up the project to outside contributions, when it makes sense.

## Features

Most of these features have been partly implemented, and are also still in progress.

General-purpose language. Special purposes can be supported by creating Domain-Specific Language dialects.

Right-level language: high-level where it can be, low-level where it needs to be. One size does not fit all.

The language adapts to the platform to support a wide range of systems. The language strongly supports to write cross-platform programs, but also has strong support for writing platform-specific programs.

Human-friendly syntax. Closer to human language than most computer languages. The current implementation is based on English, including simple math notation. (But note that this is not natural-language programming and not mind reading. You still need to learn the language.)

Good (but not perfect yet) error messages. Little waste of human brain power.

As much as possible within Meta's design model, as many errors as possible are caught early, at compile time, to reduce time needed for debugging and to increase reliability of the software.

The compiler helps with trying out and converting code from several other, related languages. It detects some words and paths from other REBOL-like languages: REBOL 3, REBOL 2, Red, Red/System and Boron, and some words from the Logo, Lisp and Scheme language families. An error message will be produced, but when there is an alternative in Meta, this will be suggested.

Influenced mostly by REBOL and other languages from the REBOL family, and further by Logo, C, Turbo-BASIC XL, MAC/65, Action!, PL65, ALGOL 68, OCaml, Miranda and Twentel, with some touches of Pascal and COBOL. The implementation is further influenced by TAOS, Plan 9, LLVM and WebAssembly. REBOL itself was mainly influenced by Lisp, Forth, Logo and Scheme, and probably also by Smalltalk, Self, NewLISP, Rexx and a bit of C and BCPL.

The language design is underpinned by the theory of denotational semantics.

The language design is homo-iconic. Code is data (once implemented).

The base language design has no grammar, or if you will, an unrestricted grammar. Dialects can be constructed from it that do have grammar. Any computer language could be constructed. To make this easier, the language does predefine the literal syntax of basic data types. This structures and standardises the form that dialects usually take.

Among the basic data types are words, much like in human language.

Since the base language has no grammar, there can be no default scoping rules. Instead, the language provides contexts, to which each instance of a word can be bound individually. Dialects can use this system of words, word instances and contexts to construct their own scoping rules.

The default language dialect, which we call the do dialect, is an impure functional language, that also supports imperative programming, assisted by several embedded specification dialects.

The functional language is a context-sensitive language, whereas most computer languages are more limited context-free languages. Some are even more limited regular languages.

The functional language is based on multi-methods.

The functional language supports parenthesised and parenthesis-free prefix symbolic expressions and infix operators.

The functional language uses a special form of static/lexical scoping, called definitional scoping by REBOL's inventor.

Light-weight abstractions of both native and external data types.

The type system currently uses strong static typing, providing type safety with type inference, and will be extended to gradual typing.

Elegant option types.

Efficient range types/slices, avoiding unnecessary copying.

The functional language will be memory safe (once implemented).

The functional language uses one-based indexing. Compared to zero-based indexing, this is the human-friendly choice. However, it is not hard to do zero-based indexing.

The language seamlessly integrates a 6502/6507 assembler dialect for systems that have this processor.

Ahead-Of-Time compiler that does whole-program optimisation.

The language implementation is designed around an Intermediate Representation.

Multiple code generation back-ends: C transpiler, proofs of concept for WebAssembly and 6502/6507 machine code.

The compiler produces stand-alone, freely distributable executable programs or web pages. Any needed parts of the Meta runtime are compiled in.

Easy use through a remote build service and a web console. No complex toolchains to install, modify, configure and keep updated on your systems. We do that for you on our build server.

Rapid development of the language through continuous deployment.

The compiler client is currently available for web browsers, Windows, Apple MacOS, Linux, FreeBSD, NetBSD and OpenBSD.

The compiler currently produces programs for web browsers, PC platforms and for Atari 8-bit home computers. Stay tuned for more.


https://language.metaproject.frl

#meta-lang #allerrorsmatter #cod-ape #meta-cod #cod-meta #metalyzed
