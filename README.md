## Installation
### Shell alias definition
Tested on ZSH : \
`alias pype='python3 -c"import sys,re;[print(eval(sys.argv[1]),end=\"\") for line in sys.stdin]"'`

## Examples
### HTMLize
`alias htmlize='pype "line.encode(\"ascii\", \"xmlcharrefreplace\").decode(\"UTF-8\")"'`

$ `echo "Et voilà" | htmlize` \
Et voil\&#224;

### Mass rename with field re-ordering based on regexp matching

$ `ls` \
1._Hazem-TAL55-1.pdf \
1-Lavallee-TAL52-2-2011.pdf \
1-Marsic-TAL53-2.pdf \
1.Maynard-TAL55-2.pdf

$`ls | pype 're.search("^[^T].*(?:TAL)?.{,2}(\d(\d))-(\d).*", line).expand("mv \g<0> TAL-201\g<2>-\g<1>-\g<2>-\g<0>\n")'` \
mv 1._Hazem-TAL55-1.pdf TAL-2015-55-5-1._Hazem-TAL55-1.pdf \
mv 1-Lavallee-TAL52-2-2011.pdf TAL-2012-52-2-1-Lavallee-TAL52-2-2011.pdf \
mv 1-Marsic-TAL53-2.pdf TAL-2013-53-3-1-Marsic-TAL53-2.pdf \
mv 1.Maynard-TAL55-2.pdf TAL-2015-55-5-1.Maynard-TAL55-2.pdf

Here you still need to copy/paste the built mv commands to actually execute them.

***

To be continued…
