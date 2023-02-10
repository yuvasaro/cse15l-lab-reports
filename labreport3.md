# Lab Report 3 - Researching Commands

## Grep Command



### [1] (Source: ChatGPT)

```bash
grep -r "search_string" directory/
```

The `-r` tag means search recursively, or search all files and folders within a directory including 
subfolders.

```bash
grep -r "Lucayans" written_2
```

```
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```

This code searches for all files in `written_2` that have the string "Lucayans" and prints out all
the lines containing the string.

Combining the `-r` tag with the `-l` tag that lists the files that contain the given string:

```bash
grep -rl "Christopher Columbus" written_2
```

```
written_2/travel_guides/berlitz1/IntroMadeira.txt
written_2/travel_guides/berlitz1/HistoryMallorca.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz1/HistoryMadeira.txt
written_2/travel_guides/berlitz1/WhereToMadeira.txt
written_2/travel_guides/berlitz1/HistoryIbiza.txt
written_2/travel_guides/berlitz1/HistoryFWI.txt
written_2/travel_guides/berlitz1/WhereToMadrid.txt
written_2/travel_guides/berlitz1/WhereToFWI.txt
written_2/travel_guides/berlitz2/Costa-History.txt
written_2/travel_guides/berlitz2/Costa-WhereToGo.txt
written_2/travel_guides/berlitz2/Barcelona-History.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Barcelona-WhereToGo.txt
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt
written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt
written_2/travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
written_2/travel_guides/berlitz2/CanaryIslands-History.txt
written_2/travel_guides/berlitz2/Cuba-History.txt
```

This code searches all the files for "Christopher Columbus" and lists all the files that contain it.



### [2] (Source: ChatGPT, [linuxize.com](https://linuxize.com/post/regular-expressions-in-grep/))

```bash
grep -E "^[0-9]+$" file.txt
```

The `-E` tag means to search for a regular expression. A regular expression is a string with symbols 
that represent certain searching criteria. For example, the `^` (caret) symbol means match the string 
following the symbol if it is located at the start of a line.

```bash
grep -E "^Despite" written_2/non-fiction/OUP/Berk/ch1.txt
```

```
Despite being well educated, intent on doing what’s best for their children, and enlightened by a vast literature of child-rearing advice, many American parents appear uneasy and unsure of their roles at best, baed and bewildered at worst. As the above sampling of concerns reveals, today’s parents are not just worried about major transitions and traumas, such as the impact of marital breakup or community violence. They agonize over commonplace, recurrent, everyday situations—whether intensive preschool academic tutoring is crucial for later success in school, the meaning of “quality time” with children, and whether and how to help their child with homework. At an even more fundamental level, contemporary parents have begun to doubt their own ecacy in their children’s development. Why is this so?
Despite Piaget’s overwhelming legacy, his theory has been challenged. Recent evidence indicates that Piaget underestimated the capabilities of infants and preschoolers and the direct contribution of adults—both parents and teachers—to cognitive change. To illustrate, let’s look at preschoolers’ responses to Piaget’s conservation problems—the best-known examples of the odd logic of his preoperational stage. Shown two rows of six pennies each, after which the pennies in one row are spread out in a longer line, a 4-year-old is likely to say that the longer row has more pennies. Similarly, after a large ball of play dough is divided into six smaller pieces, a preschooler usually insists that the six pieces have more play dough than the ball, even though none was added during the transformation. Yet a wealth of research reveals that when such tasks are scaled down in diculty (for example, using rows of three or four pennies rather than six or seven) or made relevant to children’s everyday experiences (pretending the play dough is cupcake batter and the six pieces are little cupcakes), preschoolers’ understandings appear closer to those of older children and adults than Piaget assumed.33
Despite grim work lives, Rosie and Henry, who had little schooling themselves, sent nine of their children to college and some to graduate school. They managed to be involved and caring parents, without all the comforts and time-saving conveniences that we now take for granted—a water-tight roof; central heating; fast foods; microwaves; vacuum cleaners; washing machines and dryers; automobiles; telephones; and much, much more.
```

This code searches for the word "Despite" at the beginning of lines in the file and returns all the
occurrences.

We can also search for all files in a directory containing a certain regular expression with `grep -rlE
<regex> <directory>`:

```bash
grep -rlE "^Despite" written_2
```

```
written_2/non-fiction/OUP/Berk/ch2.txt
written_2/non-fiction/OUP/Berk/ch1.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt
written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2/travel_guides/berlitz2/Crete-WhereToGo.txt
written_2/travel_guides/berlitz2/Budapest-WhereoGo.txt
written_2/travel_guides/berlitz2/Paris-WhereToGo.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
written_2/travel_guides/berlitz2/Budapest-WhatToDo.txt
written_2/travel_guides/berlitz2/Cancun-History.txt
written_2/travel_guides/berlitz2/Algarve-Intro.txt
written_2/travel_guides/berlitz2/China-History.txt
written_2/travel_guides/berlitz2/Canada-History.txt
written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt
```

This result shows all the files that have the string "Despite" at the beginning of one or more of their
lines.



### [3] (Source: ChatGPT)

```bash
grep -n "search_string" directory/
```

The `-n` tag means to get the line number in a file where a match was found.

```bash
grep -n "Shopping" written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt
```

```
6:Shopping
8:Shopping is also extremely pleasant in Barcelona, as the city hasn’t yet been overtaken by large look-alike malls and homogenous American or Euro stores. Catalonia still thrives on family-owned shops, and window shopping along the Rambla de Catalunya or Passeig de Gràcia is a delight. Remember that with the exception of the big department stores, most shops are closed between 1:30 or 2pm and 4 or 5pm, and stay open until 8pm or later. Many smaller stores also close Saturday afternoons and Sundays.
```

Here the word "Shopping" is found on two lines in this text file.

We can combine the `-n` tag with the `-r` tag to find all the line numbers of the files in the directory 
containing the string:

```bash
grep -rn "amusement parks" written_2
```

```
written_2/travel_guides/berlitz2/Budapest-WhereoGo.txt:123:Just behind the baths are the zoo and two amusement parks. The zoo welcomes visitors with an Art Nouveau entrance decorated with polar bears and elephants. It keeps a wide range of animals, including most children’s and adults’ favourite species. The animals are mostly held in traditional cages, though renovations on several pavilions are in progress. Grown-ups may like to note that next to the zoo is Gundel’s restaurant, a legend in Hungarian culinary circles.
written_2/travel_guides/berlitz2/Budapest-WhereoGo.txt:124:Vidám Park, next door, is an old-fashioned, funfair-style amusement park for the kids. You won’t ﬁnd American-style thrill rides here, just carousels, dodgem cars, a ferris wheel, and a few other low-technology sources of fun. A mini-version of the park more suited for younger children adjoins it. Next door to the amusement parks, a circus makes regular appearances throughout the year. For dates consult Programme magazine (see page 118). 
written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt:46:Barcelona is an excellent city for children. Besides the city beaches, the Port Vell waterfront has L’Aquàrium, the largest aquarium in Europe (along the Moll d’Espanya; Tel. 93/221 74 74), a 3-D Imax movie theater (Tel. 902/33 22 11), and lots of adolescent diversions in the Maremagnum mall—even getting there, crossing the wooden drawbridge Rambla del Mar, is fun. The Zoo (Parc Zoológic, on Ciutadella Park, Tel. 93/221 25 06), has the world’s only albino gorilla in captivity. Poble Espanyol (Avda. del Marqués de Comillas, on Montjuïc), a re-creation of a Spanish village with architectural styles from all over Spain, is very popular with families. The amusement parks on both Montjuïc and Tibidabo (Parc d’Atraccions) are very entertaining, and kids love to arrive at the former via aerial cable car (see page 69). 
written_2/travel_guides/berlitz2/Costa-WhatToDo.txt:48:Tour operators offer any number of excursions, some more esoteric than others, with brochures and booking facilities available through your hotel or a local travel agent. Another form of organized entertainment, amusement parks, are discussed below in the section for families with young children.
```

Here we have found all lines of all files containing the string "amusement parks".



### [4] (Source: ChatGPT)

```bash
grep -v "search_string" directory/
```

The `-v` tag means to reverse the match, or show all the lines in a file that _don't_ contain the string.

```bash
grep -v "the" written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt
```

```




What to Do
Shopping
Barcelona is at least Madrid’s equal as a shopping capital. As a city of eminent style and taste, Barcelona abounds in fashion boutiques, antiques shops, and art galleries. Design is taken very seriously here. 
entertainment
The weekly cultural guide Guía del Ocio contains up-to-date information on all entertainment in Barcelona (available at newsstands, in Spanish), while Barcelona Olé!, a monthly guide put out by Barcelona Tourism, has information on big shows and performances.
SportS
Spectator Sports
Participant sports
BARCELONA FOR CHILDREN
In terms of traditional sightseeing, both La Rambla, with its squawking birds and brilliantly attired mimes, and Parc Guëll, Gaudí’s playground for children of all ages, prove very diverting (see pages 57).



```

Here we search for all lines that don't contain the string "the", but one line with a capitalized "The" 
appears because the grep command by default is case-sensitive. To make it ignore case, we can use the
`-i` tag. This time, let's look for all lines that don't contain "the" OR "a", case-insensitive:

```bash
grep -vi "the\|a" written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt
```

```




Shopping
SportS



```

It turns out there are only two lines with text (and a bunch of empty lines) in this file that don't contain the strings "the" or "a".
