# linkparser

* http://deveiate.org/projects/Ruby-LinkParser

## Description

This module is a Ruby binding for [the Abiword version][abiword] of CMU's 
[Link Grammar][link-grammar], a syntactic parser of English. 


### Example Usage

	require 'linkparser'
	
	dict = LinkParser::Dictionary.new( :screen_width => 100 )
	sent = dict.parse( "People use Ruby for all kinds of nifty things." )
	# => #<LinkParser::Sentence:0xcf8eb "LEFT-WALL people use Ruby for all kinds
	#      of nifty things . RIGHT-WALL"/2 linkages/0 nulls>
	
	sent.subject        # => "people"
	sent.verb           # => "use"
	sent.object         # => "Ruby"
	
	puts sent.constituent_tree_string
	# =>
	# (S (NP People)
	#    (VP use
	#        (NP Ruby)
	#        (PP for
	#            (NP (NP all kinds)
	#                (PP of
	#                    (NP nifty things)))))
	#    .)
	
	puts sent.diagram
	# =>
	#     +-------------------------------Xp------------------------------+
	#     |                +----MVp---+----Jp----+     +------Jp-----+    |
	#     +----Wd---+--Sp--+--Os-+    |    +-Dmc-+--Mp-+    +----A---+    |
	#     |         |      |     |    |    |     |     |    |        |    |
	# LEFT-WALL people.p use.v Ruby for.p all kinds.n of nifty.a things.n . 


## Installation

First, download and install the latest version of the link-grammar 
library from [Abiword's site][abiword-dl].

Then install the gem:

    gem install linkparser

You may need to specify the path to the link-grammar library if you 
installed it somewhere that your linker doesn't look by default:

    gem install linkparser -- --with-link-grammar=/usr/local


## Contributing

You can check out the current development source [with Mercurial][hg-repo],
or if you prefer Git, via [its Github mirror][github-mirror].

After checking out the source, run:

	$ rake newb

This task will install any missing dependencies, run the tests/specs,
and generate the API documentation.


## License

Copyright (c) 2006-2011, The FaerieMUD Consortium
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice,
  this list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice,
  this list of conditions and the following disclaimer in the documentation
  and/or other materials provided with the distribution.

* Neither the name of the author/s, nor the names of the project's
  contributors may be used to endorse or promote products derived from this
  software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


[abiword]:http://www.abisource.com/projects/link-grammar/
[link-grammar]:http://www.link.cs.cmu.edu/link/ "Link Grammar"
[abiword-dl]:http://www.abisource.com/projects/link-grammar/#download
[hg-repo]:http://repo.deveiate.org/LinkParser
[github-mirror]:http://github.com/ged/linkparser
