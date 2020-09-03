---
title: Informations de référence sur les symboles et les opérateurs
description: 'En savoir plus sur les symboles et les opérateurs utilisés dans le langage de programmation F #.'
ms.date: 08/15/2020
fl_keywords:
- '|>_FS'
ms.openlocfilehash: 5943352f0a1710ba7a666a79b7871b7269c75a6b
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359088"
---
# <a name="symbol-and-operator-reference"></a>Informations de référence sur les symboles et les opérateurs

Cet article comprend un tableau des symboles et des opérateurs utilisés dans le langage F #.

## <a name="table-of-symbols-and-operators"></a>Tableau des symboles et des opérateurs

Le tableau suivant décrit les symboles utilisés dans le langage F # et fournit une brève description de certaines des utilisations du symbole et des liens pour plus d’informations. Les symboles sont classés selon l'ordre du jeu de caractères ASCII.

|Symbole ou opérateur|Liens|Description|
|------------------|-----|-----------|
|`!`|[Cellules de référence](../reference-cells.md)<br /><br />[Expressions de calcul](../computation-expressions.md)|<ul><li>Déréférence une cellule de référence.<br /></li><li>Après un mot clé, indique une version modifiée du comportement du mot clé sous le contrôle d'un flux de travail.<br /></li></ul>|
|`!=`||<ul><li>Non utilisé en F#. Utilisez `<>` pour les opérations d'inégalité.<br /></li></ul>|
|`"`|[Littéraux](../literals.md)<br /><br />[Chaînes](../strings.md)|<ul><li>Délimite une chaîne de texte.<br /></li></ul>|
|`"""`|[Chaînes](../strings.md)|Délimite une chaîne textuelle. Diffère de `@"..."` en ce sens que vous pouvez indiquer un caractère guillemet anglais en utilisant un seul guillemet dans la chaîne.|
|`#`|[Directives de compilateur](../compiler-directives.md)<br /><br />[Types flexibles](../flexible-types.md)|<ul><li>Préfixe une directive de préprocesseur ou de compilateur, telle que `#light`.<br /></li><li>Quand il est utilisé avec un type, indique un *type flexible* qui fait référence à un type ou à l’un de ses types dérivés.<br /></li></ul>|
|`$`||<ul><li>Utilisé en interne pour certains noms de variable et de fonction générés par le compilateur.<br /></li></ul>|
|`%`|[Opérateurs arithmétiques](arithmetic-operators.md)<br /><br />[Quotations de code](../code-quotations.md)|<ul><li>Calcule le reste entier.<br /></li><li>Utilisée pour les expressions d'ajout dans les quotations de code typé.<br /></li></ul>|
|`%%`|[Quotations de code](../code-quotations.md)|<ul><li>Utilisée pour les expressions d'ajout dans les quotations de code non typé.<br /></li></ul>|
|`%?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Calcule le reste entier, lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`&`|[Expressions de correspondance](../match-expressions.md)|<ul><li>Calcule l'adresse d'une valeur mutable pour une utilisation lors de l'interaction avec d'autres langages.<br /></li><li>Utilisé dans les modèles AND.<br /></li></ul>|
|`&&`|[Opérateurs booléens](boolean-operators.md)|<ul><li>Calcule l'opération booléenne AND.<br /></li></ul>|
|`&&&`|[Opérateurs au niveau du bit](bitwise-operators.md)|<ul><li>Calcule l'opération AND au niveau du bit.<br /></li></ul>|
|`'`|[Littéraux](../literals.md)<br /><br />[Généralisation automatique](../generics/automatic-generalization.md)|<ul><li>Délimite un littéral à un seul caractère.<br /></li><li>Indique un paramètre de type générique.<br /></li></ul>|
|<code>&#96;&#96;...&#96;&#96;</code>||<ul><li>Délimite un identificateur qui, sinon, ne serait pas un identificateur légal, tel qu'un mot clé du langage.<br /></li></ul>|
|`( )`|[Unit, type](../unit-type.md)|<ul><li>Représente la valeur unique du type d'unité.<br /></li></ul>|
|`(...)`|[Tuples](../tuples.md)<br /><br />[Surcharge d’opérateur](../operator-overloading.md)|<ul><li>Indique l'ordre dans lequel les expressions sont analysées.<br /></li><li>Délimite un tuple.<br /></li><li>Utilisé dans les définitions d'opérateur.<br /></li></ul>|
|`(*...*)`||<ul><li>Délimite un commentaire qui peut couvrir plusieurs lignes.<br /></li></ul>|
|<code>(&#124;...&#124;)</code>|[Modèles actifs](../active-patterns.md)|<ul><li>Délimite un modèle actif. Également appelés *« banana clips »*.<br /></li></ul>|
|`*`|[Opérateurs arithmétiques](arithmetic-operators.md)<br /><br />[Tuples](../tuples.md)<br /><br />[Unités de mesure](../units-of-measure.md)|<ul><li>Lorsqu'il est utilisé comme un opérateur binaire, multiplie les côtés gauche et droit.<br /></li><li>Dans les types, indique un jumelage dans un tuple.<br /></li><li>Utilisé dans les types d'unités de mesure.<br /></li></ul>|
|`*?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Multiplie les côtés gauche et droit, lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`**`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Calcule l’opération d’élévation à la puissance (`x ** y` signifie `x` puissance `y`).<br /></li></ul>|
|`+`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Lorsqu'il est utilisé comme opérateur binaire, ajoute les côtés gauche et droit.<br /></li><li>Lorsqu'il est utilisé comme opérateur unaire, indique une quantité positive. (Formellement, il produit la même valeur avec le signe inchangé.)<br /></li></ul>|
|`+?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Ajoute les côtés gauche et droit, lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`,`|[Tuples](../tuples.md)|<ul><li>Sépare les éléments d’un tuple, ou les paramètres de type.<br /></li></ul>|
|`-`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Lorsqu'il est utilisé comme opérateur binaire, soustrait le côté droit du côté gauche.<br /></li><li>Lorsqu'il est utilisé comme opérateur unaire, effectue une opération de négation.<br /></li></ul>|
|`-?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Soustrait le côté droit du côté gauche, lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`->`|[Fonctions](../functions/index.md)<br /><br />[Expressions de correspondance](../match-expressions.md)|<ul><li>Dans les types de fonction, délimite les arguments et les valeurs de retour.<br /></li><li>Génère une expression (dans les expressions de séquence) ; équivalent au mot clé `yield`.<br /></li><li>Utilisé dans les expressions de correspondance<br /></li></ul>|
|`.`|[Members](../members/index.md) (Membres)<br /><br />[Types primitifs](../basic-types.md)|<ul><li>Accède à un membre et sépare les noms individuels dans un nom complet.<br /></li><li>Spécifie une virgule décimale dans les nombres à virgule flottante.<br /></li></ul>|
|`..`|[Boucles : expression `for...in`](../loops-for-in-expression.md)|<ul><li>Spécifie une plage.<br /></li></ul>|
|`.. ..`|[Boucles : expression `for...in`](../loops-for-in-expression.md)|<ul><li>Spécifie une plage et un incrément.<br /></li></ul>|
|`.[...]`|[Tableaux](../arrays.md)|<ul><li>Accède à un élément de tableau.<br /></li></ul>|
|`/`|[Opérateurs arithmétiques](arithmetic-operators.md)<br /><br />[Unités de mesure](../units-of-measure.md)|<ul><li>Divise le côté gauche (numérateur) par le côté droit (dénominateur).<br /></li><li>Utilisé dans les types d'unités de mesure.<br /></li></ul>|
|`/?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Divise le côté gauche par le côté droit lorsque ce dernier est un type Nullable.<br /></li></ul>|
|`//`||<ul><li>Indique le début d'un commentaire sur une ligne.<br /></li></ul>|
|`///`|[Documentation XML](../xml-documentation.md)|<ul><li>Indique un commentaire XML.<br /></li></ul>|
|`:`|[Fonctions](../functions/index.md)|<ul><li>Dans une annotation de type, sépare un nom de paramètre ou de membre de son type.<br /></li></ul>|
|`::`|[Listes](../lists.md)<br /><br />[Expressions de correspondance](../match-expressions.md)|<ul><li>Crée une liste. L’élément côté gauche est ajouté en préfixe à la liste côté droit.<br /></li><li>Utilisé dans les critères spéciaux pour séparer les parties d’une liste.<br /></li></ul>|
|`:=`|[Cellules de référence](../reference-cells.md)|<ul><li>Assigne une valeur à une cellule de référence.<br /></li></ul>|
|`:>`|[Cast et conversions](../casting-and-conversions.md)|<ul><li>Convertit un type en un type placé plus haut dans la hiérarchie.<br /></li></ul>|
|`:?`|[Expressions de correspondance](../match-expressions.md)|<ul><li>Retourne `true` si la valeur correspond au type spécifié (y compris s’il s’agit d’un sous-type); sinon, retourne `false` (opérateur de test de type).<br /></li></ul>|
|`:?>`|[Cast et conversions](../casting-and-conversions.md)|<ul><li>Convertit un type en un type placé plus bas dans la hiérarchie.<br /></li></ul>|
|`;`|[Syntaxe détaillée](../verbose-syntax.md)<br /><br />[Listes](../lists.md)<br /><br />[Enregistrements](../records.md)|<ul><li>Sépare les expressions (utilisé principalement dans la syntaxe des commentaires).<br /></li><li>Sépare les éléments d'une liste.<br /></li><li>Sépare les champs d'un enregistrement.<br /></li></ul>|
|`<`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Calcule l'opération « inférieur à ».<br /></li></ul>|
|`<?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|Calcule l'opération « inférieur à » lorsque la partie droite est un type Nullable.|
|`<<`|[Fonctions](../functions/index.md)|<ul><li>Compose deux fonctions dans l'ordre inverse ; la deuxième est exécutée en premier (opérateur de composition arrière).<br /></li></ul>|
|`<<<`|[Opérateurs au niveau du bit](bitwise-operators.md)|<ul><li>Décale les bits de la quantité côté gauche vers la gauche selon le nombre de bits spécifié côté droit.<br /></li></ul>|
|`<-`|[Valeurs](../values/index.md)|<ul><li>Assigne une valeur à une variable.<br /></li></ul>|
|`<...>`|[Généralisation automatique](../generics/automatic-generalization.md)|<ul><li>Délimite les paramètres de type.<br /></li></ul>|
|`<>`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Retourne `true` si le côté gauche n'est pas égal au côté droit ; sinon, retourne false.<br /></li></ul>|
|`<>?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Calcule l'opération « non égal à » lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`<=`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Retourne `true` si le côté gauche est inférieur ou égal au côté droit ; sinon, retourne `false`.<br /></li></ul>|
|`<=?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Calcule l'opération « inférieur ou égal à » lorsque la partie droite est un type Nullable.<br /></li></ul>|
|<code>&#124;></code>|[Fonctions](../functions/index.md)|<ul><li>Passe le résultat du côté gauche de la fonction au côté droit (opérateur de canal avant).<br /></li></ul>|
|<code>&#124;&#124;></code>|[&#40; &#124;&#124;&#62; &#41;&#60; 't 1, 't 2 ', 'U&#62; fonction](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%7C%7C%3E%20))|<ul><li>Transmet le tuple de deux arguments côté gauche à la fonction côté droit.<br /></li></ul>|
|<code>&#124;&#124;&#124;></code>|[&#40; &#124;&#124;&#124;&#62; &#41;&#60; 't 1, 't 2, 't 3 ', 'U&#62; fonction](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%7C%7C%7C%3E%20))|<ul><li>Transmet le tuple de trois arguments côté gauche à la fonction côté droit.<br /></li></ul>|
|<code>&lt;&#124;</code>|[Fonctions](../functions/index.md)|<ul><li>Passe le résultat de l'expression côté droit à la fonction côté gauche (opérateur de barre verticale inverse).<br /></li></ul>|
|<code>&lt;&#124;&#124;</code>|[&#40; &#60;&#124;&#124; &#41;&#60; 't 1, 't 2 ', 'U&#62; fonction](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%3C%7C%7C%20))|<ul><li>Transmet le tuple de deux arguments côté droit à la fonction côté gauche.<br /></li></ul>|
|<code>&lt;&#124;&#124;&#124;</code>|[&#40; &#60;&#124;&#124;&#124; &#41;&#60; 't 1, 't 2, 't 3 ', 'U&#62; fonction](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%3C%7C%7C%7C%20))|<ul><li>Transmet le tuple de trois arguments côté droit à la fonction côté gauche.<br /></li></ul>|
|`<@...@>`|[Quotations de code](../code-quotations.md)|<ul><li>Délimite une quotation de code typé.<br /></li></ul>|
|`<@@...@@>`|[Quotations de code](../code-quotations.md)|<ul><li>Délimite une quotation de code non typé.<br /></li></ul>|
|`=`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Retourne `true` si le côté gauche est égal au côté droit ; sinon, retourne `false`.<br /></li></ul>|
|`=?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Calcule l'opération « égal à » lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`==`||<ul><li>Non utilisé en F#. Utilisez `=` pour les opérations d'égalité.<br /></li></ul>|
|`>`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Retourne `true` si le côté gauche est supérieur au côté droit ; sinon, retourne `false`.<br /></li></ul>|
|`>?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Calcule l’opération « supérieur à » lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`>>`|[Fonctions](../functions/index.md)|<ul><li>Compose deux fonctions (opérateur de composition avant).<br /></li></ul>|
|`>>>`|[Opérateurs au niveau du bit](bitwise-operators.md)|<ul><li>Décale les bits de la quantité côté gauche vers la droite selon le nombre d'emplacements spécifié côté droit.<br /></li></ul>|
|`>=`|[Opérateurs arithmétiques](arithmetic-operators.md)|<ul><li>Retourne `true` si le côté gauche est supérieur ou égal au côté droit ; sinon, retourne `false` .<br /></li></ul>|
|`>=?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Calcule l'opération « supérieur ou égal à » lorsque la partie droite est un type Nullable.<br /></li></ul>|
|`?`|[Paramètres et arguments](../parameters-and-arguments.md)|<ul><li>Spécifie un argument facultatif.<br /></li><li>Utilisé comme opérateur pour les appels de méthodes et de propriétés dynamiques. Vous devez fournir votre propre implémentation.<br /></li></ul>|
|`? ... <- ...`||<ul><li>Utilisé comme opérateur pour définir les propriétés dynamiques. Vous devez fournir votre propre implémentation.<br /></li></ul>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Équivaut aux opérateurs correspondants sans le suffixe ? , où un type Nullable est situé à gauche.<br /></li></ul>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Équivaut aux opérateurs correspondants sans le suffixe ? , où un type Nullable est situé à droite.<br /></li></ul>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Opérateurs autorisant la valeur Null](nullable-operators.md)|<ul><li>Équivalent aux opérateurs correspondants sans les points d'interrogation, où les deux côtés sont des types Nullables.<br /></li></ul>|
|`@`|[Listes](../lists.md)<br /><br />[Chaînes](../strings.md)|<ul><li>Concatène deux listes.<br /></li><li>Lorsqu'il est placé avant un littéral de chaîne, indique que la chaîne doit être interprétée textuellement, sans interprétation des caractères d'échappement.<br /></li></ul>|
|`[...]`|[Listes](../lists.md)|<ul><li>Délimite les éléments d'une liste.<br /></li></ul>|
|<code>[&#124;...&#124;]</code>|[Tableaux](../arrays.md)|<ul><li>Délimite les éléments d'un tableau.<br /></li></ul>|
|`[<...>]`|[Attributs](../attributes.md)|<ul><li>Délimite un attribut.<br /></li></ul>|
|`\`|[Chaînes](../strings.md)|<ul><li>Échappe le caractère suivant ; utilisé dans les littéraux de caractère et de chaîne.<br /></li></ul>|
|`^`|[Paramètres de type résolus statiquement](../generics/statically-resolved-type-parameters.md)<br /><br />[Chaînes](../strings.md)|<ul><li>Spécifie les paramètres de type qui doivent être résolus au moment de la compilation, pas au moment de l’exécution.<br /></li><li>Concatène les chaînes.<br /></li></ul>|
|`^^^`|[Opérateurs au niveau du bit](bitwise-operators.md)|<ul><li>Calcule l'opération OR exclusif au niveau du bit.<br /></li></ul>|
|`_`|[Expressions de correspondance](../match-expressions.md)<br /><br />[Génériques](../generics/index.md)|<ul><li>Indique un modèle de caractère générique.<br /></li><li>Spécifie un paramètre générique anonyme.<br /></li></ul>|
|<code>&#96;</code>|[Généralisation automatique](../generics/automatic-generalization.md)|<ul><li>Utilisé en interne pour indiquer un paramètre de type générique.<br /></li></ul>|
|`{...}`|[Séquences](../sequences.md)<br /><br />[Enregistrements](../records.md)|<ul><li>Délimite les expressions de séquence et les expressions de calcul.<br /></li><li>Utilisé dans les définitions d'enregistrement.<br /></li></ul>|
|<code>&#124;</code>|[Expressions de correspondance](../match-expressions.md)|<ul><li>Délimite les cas de correspondance individuels, les cas d'union discriminés individuels et les valeurs d'énumération.<br /></li></ul>|
|<code>&#124;&#124;</code>|[Opérateurs booléens](boolean-operators.md)|<ul><li>Calcule l'opération booléenne OR.<br /></li></ul>|
|<code>&#124;&#124;&#124;</code>|[Opérateurs au niveau du bit](bitwise-operators.md)|<ul><li>Calcule l'opération OR au niveau du bit.<br /></li></ul>|
|`~~`|[Surcharge d’opérateur](../operator-overloading.md)|<ul><li>Permet de déclarer une surcharge pour l'opérateur de négation unaire.<br /></li></ul>|
|`~~~`|[Opérateurs au niveau du bit](bitwise-operators.md)|<ul><li>Calcule l'opération NOT au niveau du bit.<br /></li></ul>|
|`~-`|[Surcharge d’opérateur](../operator-overloading.md)|<ul><li>Permet de déclarer une surcharge pour l'opérateur moins unaire.<br /></li></ul>|
|`~+`|[Surcharge d’opérateur](../operator-overloading.md)|<ul><li>Permet de déclarer une surcharge pour l'opérateur plus unaire.<br /></li></ul>|

## <a name="operator-precedence"></a>Précédence des opérateurs

Le tableau suivant indique l'ordre de priorité des opérateurs et autres mots clés d'expression en langage F#, de la priorité la plus basse à la priorité la plus élevée. L'associativité est également mentionnée, le cas échéant.

|Opérateur|Associativité|
|--------|-------------|
|`as`|Right|
|`when`|Right|
|<code>&#124;</code> conduit|Gauche|
|`;`|Right|
|`let`|Non associatif|
|`function`, `fun`, `match`, `try`|Non associatif|
|`if`|Non associatif|
|`not`|Right|
|`->`|Right|
|`:=`|Right|
|`,`|Non associatif|
|`or`, <code>&#124;&#124;</code>|Gauche|
|`&`, `&&`|Gauche|
|`:>`, `:?>`|Right|
|`<`*op*, `>` *op*, `=` , <code>&#124;</code> *op*, `&` *op*,`&`<br /><br />(y compris `<<<`, `>>>`, <code>&#124;&#124;&#124;</code>, `&&&`)|Gauche|
|`^`*opérationnel*<br /><br />(y compris `^^^`)|Right|
|`::`|Right|
|`:?`|Non associatif|
|`-`*op*, `+` *op*|S'applique aux utilisations infixes de ces symboles|
|`*`*op*, `/` *op*, `%` *op*|Gauche|
|`**`*opérationnel*|Right|
|`f x` (application de fonction)|Gauche|
|<code>&#124;</code> (critères spéciaux)|Right|
|opérateurs de préfixe ( `+` *op*, `-` *op*, `%` , `%%` , `&` , `&&` , `!` *op*, `~` *op*)|Gauche|
|`.`|Gauche|
|`f(x)`|Gauche|
|`f<`*modes*`>`|Gauche|

F# prend en charge la surcharge d'opérateur personnalisé. Cela signifie que vous pouvez définir vos propres opérateurs. Dans le tableau précédent, *op* peut être une séquence valide (éventuellement vide) de caractères d’opérateur, intégrée ou définie par l’utilisateur. Par conséquent, vous pouvez utiliser ce tableau pour déterminer la séquence de caractères à utiliser pour un opérateur personnalisé et atteindre ainsi le niveau de priorité souhaité. Les caractères `.` de tête sont ignorés lorsque le compilateur détermine les priorités.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](../index.md)
- [Surcharge d’opérateur](../operator-overloading.md)
