# PHYLIP multiple sequence alignment format (skbio.io.phylip)
The PHYLIP file format stores a multiple sequence alignment. The format was originally defined and used in Joe Felsenstein’s PHYLIP package [R165], and has since been supported by several other bioinformatics tools (e.g., RAxML [R166]). See [R167] for the original format description, and [R168] and [R169] for additional descriptions.

An example PHYLIP-formatted file taken from [R167]:
```
      5    42
Turkey    AAGCTNGGGC ATTTCAGGGT GAGCCCGGGC AATACAGGGT AT
Salmo gairAAGCCTTGGC AGTGCAGGGT GAGCCGTGGC CGGGCACGGT AT
H. SapiensACCGGTTGGC CGTTCAGGGT ACAGGTTGGC CGTTCAGGGT AA
Chimp     AAACCCTTGC CGTTACGCTT AAACCGAGGC CGGGACACTC AT
Gorilla   AAACCCTTGC CGGTACGCTT AAACCATTGC CGGTACGCTT AA
```
Note

Original copyright notice for the above PHYLIP file:

(c) Copyright 1986-2008 by The University of Washington. Written by Joseph Felsenstein. Permission is granted to copy this document provided that no fee is charged for it and that this copyright notice is not removed.

Format Support
Has Sniffer: No

Reader	Writer	Object Class
No	Yes	skbio.alignment.Alignment
## Format Specification
PHYLIP format is a plain text format containing exactly two sections: a header describing the dimensions of the alignment, followed by the multiple sequence alignment itself.

The format described here is “strict” PHYLIP, as described in [R168]. Strict PHYLIP requires that each sequence identifier is exactly 10 characters long (padded with spaces as necessary). Other bioinformatics tools (e.g., RAxML) may relax this rule to allow for longer sequence identifiers. See the Alignment Section below for more details.

The format described here is “sequential” format. The original PHYLIP format specification [R167] describes both sequential and interleaved formats.

Note

scikit-bio currently only supports writing strict, sequential PHYLIP-formatted files from an skbio.alignment.Alignment. It does not yet support reading PHYLIP-formatted files, nor does it support relaxed or interleaved PHYLIP formats.

Header Section
The header consists of a single line describing the dimensions of the alignment. It must be the first line in the file. The header consists of optional spaces, followed by two positive integers (n and m) separated by one or more spaces. The first integer (n) specifies the number of sequences (i.e., the number of rows) in the alignment. The second integer (m) specifies the length of the sequences (i.e., the number of columns) in the alignment. The smallest supported alignment dimensions are 1x1.

Note

scikit-bio will write the PHYLIP format header without preceding spaces, and with only a single space between n and m.

PHYLIP format does not support blank line(s) between the header and the alignment.

Alignment Section
The alignment section immediately follows the header. It consists of n lines (rows), one for each sequence in the alignment. Each row consists of a sequence identifier (ID) and characters in the sequence, in fixed width format.

The sequence ID can be up to 10 characters long. IDs less than 10 characters must have spaces appended to them to reach the 10 character fixed width. Within an ID, all characters except newlines are supported, including spaces, underscores, and numbers.

Note

While not explicitly stated in the original PHYLIP format description, scikit-bio only supports writing unique sequence identifiers (i.e., duplicates are not allowed). Uniqueness is required because an skbio.alignment.Alignment cannot be created with duplicate IDs.

scikit-bio supports the empty string ('') as a valid sequence ID. An empty ID will be padded with 10 spaces.

Sequence characters immediately follow the sequence ID. They must start at the 11th character in the line, as the first 10 characters are reserved for the sequence ID. While PHYLIP format does not explicitly restrict the set of supported characters that may be used to represent a sequence, the original format description [R167] specifies the IUPAC nucleic acid lexicon for DNA or RNA sequences, and the IUPAC protein lexicon for protein sequences. The original PHYLIP specification uses - as a gap character, though older versions also supported .. The sequence characters may contain optional spaces (e.g., to improve readability), and both upper and lower case characters are supported.

Note

scikit-bio will write a PHYLIP-formatted file even if the alignment’s sequence characters are not valid IUPAC characters. This differs from the PHYLIP specification, which states that a PHYLIP-formatted file can only contain valid IUPAC characters. To check whether all characters are valid before writing, the user can call Alignment.is_valid().

Since scikit-bio supports both - and . as gap characters (e.g., in skbio.alignment.Alignment), both are supported when writing a PHYLIP-formatted file.

When writing a PHYLIP-formatted file, scikit-bio will split up each sequence into chunks that are 10 characters long. Each chunk will be separated by a single space. The sequence will always appear on a single line (sequential format). It will not be wrapped across multiple lines. Sequences are chunked in this manner for improved readability, and because most example PHYLIP files are chunked in a similar way (e.g., see the example file above). Note that this chunking is not required by the PHYLIP format.



References
[R165]	http://evolution.genetics.washington.edu/phylip.html
[R166]	RAxML Version 8: A tool for Phylogenetic Analysis and Post-Analysis of Large Phylogenies”. In Bioinformatics, 2014
[R167]	http://evolution.genetics.washington.edu/phylip/doc/sequence.html
[R168]	http://www.phylo.org/tools/obsolete/phylip.html
[R169]	http://www.bioperl.org/wiki/PHYLIP_multiple_alignment_format
Back to top
© Copyright 2014--, scikit-bio development team.
Created using Sphinx 1.2.2.
