                                                                                                
## XML extensible Markup Language

# TP xpath xml


1 Les pays de plus de 6000000 habitants :

    *   //country[population>6000000]/name

2 Codes des pays bordant la France

    *   //country[name="France"]/border


3 Nombre de provinces en France ?

    *    //country[name="France"]/count(province)




Caractéristiques de Paris ?

//city[name="Paris"]
Le nom et la population de la 3ème ville de France dans l'ordre du document.

//country[@car_code="F"]//city[3]
//country[@car_code="F"]//city[3]/(name,population[last()])
Toutes les religions, sans doublons.

distinct-values(//country/province)
Noms des pays bordant la France

//country[name="France"]/border/@country
les pays frontaliers communs à l'Allemagne et à la France.

for $a in doc("mondial.xml")//country[@car_code="D"]/border/@country
for $f in doc("mondial.xml")//country[@car_code="F"]/border/@country
where $a=$f return data($f)
Combien de fois la superficie de la France fait celle du Luxenbourg ?

let $a:=doc("mondial.xml")//country[name="France"]/@area let $b:=doc("mondial.xml")//country[name="Luxembourg"]/@area return $a div $b
Quelle est la superficie de l'Europe ?

sum(//country[encompassed[@continent="europe"]]/@area)
Quel est la population de l’Afrique ?

sum(//country[encompassed[@continent="africa"]]/population[last()])
Combien de pays a-t-on en afrique ?

count(//country[encompassed[@continent="africa"]])
Quel sont les pays traversés par le Mississippi?

//river[name="Mississippi"]/@country
Quel sont les pays qui bordent France ??

//country[name="France"]/border/@country
Combien et quels sont les pays qui E à plus d’un continent ?

//country[count(encompassed)>1]/name
Quels sont les pays limitrophes de l’Allemagne ?

//country[name="Germany"]/border/@country
Quel est le pays ou la population est la plus dense ?

//country[population[last()]=max(//country/population[last()])]