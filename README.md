Download Link: https://assignmentchef.com/product/solved-csc349-assignment-6-dynamic-programming
<br>
Many problems in bioinformatics amount to approximate string matching. For example, whenever a new gene is sequenced, searching known genes for close matches allows us to attempt to infer the new gene’s functions.

<strong>Deliverables:</strong>

<strong>GitHub Classroom: </strong><a href="https://classroom.github.com/a/1wR915rB">https://classroom.github.com/a/1wR915rB</a>

<strong>Required Files:                   </strong>compile.sh, run.sh

<strong>Optional Files:                           </strong>*.py, *.java, *.clj, *.kt, *.js, *.sh

<h1>Part 1: Sequence Alignment</h1>

Specifically, a gene is a string over the alphabet <sub>Σ = {</sub>A<em>,</em>C<em>,</em>G<em>,</em>T}, and the closeness of two genes is measured by the extent to which they are aligned. An <em>alignment </em>of two strings, <em><sub>x </sub></em>and <em><sub>y</sub></em>, is an arrangement of their characters in columns, in the same orders as they originally appeared, potentially interspersed by spaces.

For example, given <em><sub>x </sub></em><sub>= </sub>ACGAT and <em><sub>y </sub></em><sub>= </sub>TACGCA, one possible alignment is:

A – – – C G A T T A C G C – – A

…where the ‘-’ character is used to indicate a space. Note that a typical further requirement is that no column may contain two spaces. Another possible alignment is:

– A C G – A T T A C G C A –

Of these two alignments, the second appears to be better — certainly, it contains more exact matches. The <em>score </em>of an alignment is specified by a <sub>(</sub>|<sub>Σ</sub>| <sub>+1) </sub>× <sub>(</sub>|<sub>Σ</sub>| <sub>+1) </sub><em>scoring matrix</em>, <em><sub>δ</sub></em>. For example, the latter of the above alignments has score <em>δ</em>(-<em>,</em>T)+ <em>δ</em>(A<em>,</em>A)+ <em>δ</em>(C<em>,</em>C)+ <em>δ</em>(G<em>,</em>G)+ <em>δ</em>(-<em>,</em>C)+ <em>δ</em>(A<em>,</em>A)+ <em>δ</em>(T<em>,</em>-).

In your programming language of choice per Assignment 1, implement a dynamic programming algorithm to find the highest scoring alignment of two strings.

You may assume that both of the given strings will be non-empty and will contain only the characters ‘A’, ‘C’,

‘G’, or ‘T’. You may also assume that the scoring matrix will always contain exactly <sub>5 </sub>rows and <sub>5 </sub>columns, each in the order ‘A’, ‘C’, ‘G’, ‘T’, ‘-’, will always be symmetric about the diagonal, and will always provide integer scores.

For example, the above strings, along with a simple scoring matrix<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>, would be represented as:

ACGAT TACGCA

x A C G T A 1 0 0 0 0 C 0 1 0 0 0 G 0 0 1 0 0

T 0 0 0 1 0

– 0 0 0 0 0

Since this scoring matrix only rewards exact matches, in this situation, the second of the above alignments would indeed be better than the first (and, in fact, is the highest scoring alignment overall).

<sup>1</sup>Note that the scoring matrix is <em>not </em>your dynamic programming table; it is given to — not populated by — your algorithm.




Your program must accept as a command line argument the name of a file containing two strings and a scoring matrix as described above, then print to stdout the highest scoring alignment according to the following format:

<ul>

 <li>The first given string, assumed to be <em><sub>x</sub></em>, must be printed above the second given string, assumed to be <em><sub>y</sub></em>.</li>

 <li>The columns of the alignment must be space-separated, and ‘-’ characters<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a> must be used to represent spaces within the aligned strings. For example:</li>

</ul>

&gt;$ ./compile.sh &gt;$ ./run.sh in1.txt

x: – A C G – A T y: T A C G C A –

Score: 4

You may further assume that the highest scoring alignment will be unique. Your program will be tested using diff, so its printed output must match <em>exactly</em>.


