Forked from "code.google.com/p/python-calais" - This branch supports unicode strings and better handling of malformed urls

===================== Original Content from code.google.com hosting site ===========================================
python-calais v.1.4 -- Python interface to the OpenCalais API

This Python module is a wrapper around the OpenCalais API as documented at http://www.opencalais.com/calaisAPI by Reuters. It makes REST calls to the OpenCalais API via HTTP POST, then parses and simplifies the JSON responses returned by OpenCalais. You can then access the response data in a much more pythonic manner.

The module has only been tested with Python 2.5.

Dependencies:

    * simplejson (http://pypi.python.org/pypi/simplejson) 

Basic Usage:

To use the OpenCalais API, first create a Calais() object, passing it your OpenCalais API key and a string identifier of your application:

>>> from calais import Calais
>>> API_KEY = "your-opencalais-api-key"
>>> calais = Calais(API_KEY, submitter="python-calais demo")

You can then use the analyze() method.  It takes a string, containing the text to be analyzed by Calais and returns a CalaisResponse() object:

>>> result = calais.analyze("George Bush was the President of the United States 
of America until 2009.  Barack Obama is the new President of the United States now.")

Or you can use the analyze_url() method, which downloads the specified HTML page and passes it on to OpenCalais:

>>> result2 = calais.analyze_url("http://www.bestofsicily.com/mafia.htm")

The CalaisResponse class provides several helper methods that print information about the response:  

>>> result.print_summary()
Calais Request ID: 0bfa1f51-4dec-4a82-aba6-a9f8243a94fd
Title:
Language: English
Extractions:
        4 entities
        1 topics
        2 relations
>>> result.print_topics()
Politics
>>> result.print_entities()
Person: Barack Obama (0.29)
Country: United States of America (0.43)
Person: George Bush (0.43)
Country: United States (0.29)
>>> result.print_relations()
PersonPoliticalPast
        person:George Bush
        position:President
PersonPolitical
        person:Barack Obama
        position:President of the United States


Or you can access the results directly:

>>> print result.entities[0]["name"]
Barack Obama


You can also set processing and user directives before you make an analyze() call:

>>> calais.user_directives["allowDistribution"] = "true"
>>> result3 = calais.analyze("Some non-confidential text", external_id=calais.get_random_id())

Please report bugs or feature requests at the Google Code issue tracker for this project at http://code.google.com/p/python-calais/issues/list

This project is sponsored by A115 Ltd. (www.a115.bg/en/)
===========================================================================

NEW BSD LICENSE - http://www.opensource.org/licenses/bsd-license.php

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
