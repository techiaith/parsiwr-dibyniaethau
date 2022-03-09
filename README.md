Ymgais i ddrafftio'r ddogfennaeth:

# Parsiwr Dibyniaethau Cymraeg spaCy

Dyma gydran parsio dibyniaethau Cymraeg ar gyfer spaCy. Fe'i hyfforddwyd ar Corpws Cystrawennol y Gymraeg, sef corpws Universal Dependencies a anodwyd gan Dr Johannes Heinecke ac sydd ar gael o https://github.com/UniversalDependencies/UD_Welsh-CCG/ dan drwydded CC-BY-SA.

Yn ogystal â pharsio dibyniaethau, mae'r model hefyd yn tagio rhannau ymadrodd ac yn darparu gwybodaeth forffolegol.

Dylid nodi bod y corpws hyfforddi a ddefnyddwyd yn trin berfenwau fel enwau (h.y. ‘nouns’) yn ddieithriad, ac er bod hynny'n un dehongliad dilys, gall y ffaith bod y model yn gwneud hynny brofi’n wahanol i ddisgwyliad y sawl sydd wedi arfer trin berfenwau fel berfau o fewn cymalau berfol. Gweler https://github.com/UniversalDependencies/UD_Welsh-CCG/ am ddogfennaeth y corpws hyfforddi. Ein bwriad yn y dyfodol yw gallu darparu dadansoddiad berfol ac enwol o’r berfenw o fewn fframwaith drawsieithol Universal Dependencies.

## Gosod a Defnyddio'r Model

Er mwyn defnyddio’r gydran hon, bydda angen i chi yn gyntaf osod llyfrgell spaCy (https://spacy.io/usage), ac yna gosod y pecyn iaith Cymraeg o https://github.com/techiaith/spacy-lang-cy.

Unwaith y bydd rheini wedi eu gosod gennych, gallwch osod y model fel a ganlyn drwy lwytho'r pecyn i lawr a llywio i'r cyfeiriadur lle cafodd y ffeil ei lawrlwytho a rhedeg:

`pip install cy_ud_cy_ccg-0.0.0.tar.gz` 

Yna, o fewn sgript Python, gallwch lwytho’r model fel a ganlyn:

```
import spacy
nlp = spacy.load("cy_ud_cy_ccg")
doc = nlp("Gwelodd gath ar y fainc")
print ([("Word:", t.text, "Head:", t.head, "Dependency", t.dep_) for t in doc])
>>> [('Word:', 'Gwelodd', 'Head:', Gwelodd, 'Dependency', 'ROOT'),
     ('Word:', 'gath', 'Head:', Gwelodd, 'Dependency', 'nsubj'),
     ('Word:', 'ar', 'Head:', fainc, 'Dependency', 'case'),
     ('Word:', 'y', 'Head:', fainc, 'Dependency', 'det'),
     ('Word:', 'fainc', 'Head:', Gwelodd, 'Dependency', 'obl')]
```

I ddelweddu’r parsiad, defnyddiwch y canlynol:

```
import spacy
from spacy import displacy

nlp = spacy.load("cy_ud_cy_ccg")
doc = nlp("Gwelodd gath ar y fainc")
displacy.serve(doc, style="dep")

>>> Using the 'dep' visualizer
Serving on http://0.0.0.0:5000 ...
```
Wedyn, bydd modd i chi ymweld â http://0.0.0.0:5000 a gweld y delweddiad canlynol:

![image](https://user-images.githubusercontent.com/10194573/157477614-b58f5b8b-43d3-4e54-aead-b78e61fbc396.png)

Diolch i Lywodraeth Cymru am ariannu'r gwaith hwn fel rhan o broject Technoleg Cymraeg 2021-22. 

# Welsh Dependency Parser for spaCy

This is a Welsh-language Dependency Parser for spaCy. It was trained on Corpws Cystrawennol y Gymraeg, a Universal Dependencies corpus annotated by Dr Johannes Heinecke which is available from https://github.com/UniversalDependencies/UD_Welsh-CCG/ under a CC-BY-SA licence.

In addition to parsing dependencies, the model also tags parts of speech and provides morphological information.

Note that the training corpus used treats verbnouns as nouns without exception, and whilst this is a valid analysis, the model's adherence to this practice may be unexpected to those used to treating verbnouns as verbs within verb phrases. In the future, we intend to enable both analyses within Universal Dependencies' crosslingual framework. 

## Installing and Using the Model

To use this component, you should first install the spaCy library (https://spacy.io/usage), and then install the Welsh language pack from https://github.com/techiaith/spacy-lang-cy.

Once these are installed, install the model as follows after downloading the package and navigating to directory where the file was downloaded:

`pip install cy_ud_cy_ccg-0.0.0.tar.gz` 

Then, within a Python script, the model can be loaded and used as follows:

```
import spacy
nlp = spacy.load("cy_ud_cy_ccg")
doc = nlp("Gwelodd gath ar y fainc")
print ([("Word:", t.text, "Head:", t.head, "Dependency", t.dep_) for t in doc])
>>> [('Word:', 'Gwelodd', 'Head:', Gwelodd, 'Dependency', 'ROOT'),
     ('Word:', 'gath', 'Head:', Gwelodd, 'Dependency', 'nsubj'),
     ('Word:', 'ar', 'Head:', fainc, 'Dependency', 'case'),
     ('Word:', 'y', 'Head:', fainc, 'Dependency', 'det'),
     ('Word:', 'fainc', 'Head:', Gwelodd, 'Dependency', 'obl')]
```

To visualize the parse, use the following code:

```
import spacy
from spacy import displacy

nlp = spacy.load("cy_ud_cy_ccg")
doc = nlp("Gwelodd gath ar y fainc")
displacy.serve(doc, style="dep")

>>> Using the 'dep' visualizer
Serving on http://0.0.0.0:5000 ...
```

This will enable you to visit http://0.0.0.0:5000 in your browser and see the following:

![image](https://user-images.githubusercontent.com/10194573/157477641-fdd7e07e-e6f7-421a-9233-df13b3f9d90b.png)

We thank the Welsh Government for funding this work as part of the Technoleg Cymraeg 2021-22 project.
