                                                                                                
## XML extensible Markup Language

# TP xpath xml



Combien de fois la superficie de la France fait celle du Luxenbourg ?

    * let $a:=doc("mondial.xml")//country[name="France"]/@area let $b:=doc("mondial.xml")//country[name="Luxembourg"]/@area return $a div $b


Quelle est la superficie de l'Europe ?

    * sum(//country[encompassed[@continent="europe"]]/@area)
      Quel est la population de l’Afrique ?

      sum(//country[encompassed[@continent="africa"]]/population[last()])

Combien de pays a-t-on en afrique ?

    *  count(//country[encompassed[@continent="africa"]])

Quel sont les pays traversés par le Mississippi?

    *   //river[name="Mississippi"]/@country


Quel sont les pays qui bordent France ??

     *  //country[name="France"]/border/@country


Combien et quels sont les pays qui E à plus d’un continent ?

     *  //country[count(encompassed)>1]/name

Quels sont les pays limitrophes de l’Allemagne ?

    * //country[name="Germany"]/border/@country


Quel est le pays ou la population est la plus dense ?

    *  //country[population[last()]=max(//country/population[last()])]