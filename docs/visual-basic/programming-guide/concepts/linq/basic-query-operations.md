---
title: Opérations de requête de base
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266376"
---
# <a name="basic-query-operations-visual-basic"></a>Opérations de requête de base (Visual Basic)
Ce sujet fournit une brève introduction aux expressions de la requête intégrée en langue (LINQ) dans Visual Basic, et à certains des types typiques d’opérations que vous effectuez dans une requête. Pour plus d'informations, voir les rubriques suivantes :  
  
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Requêtes](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Procédure pas à pas : écriture de requêtes dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Spécifier la source de données (à partir de)  
 Dans une requête LINQ, la première étape consiste à spécifier la source de données que vous souhaitez interroger. Par conséquent, la `From` clause dans une requête vient toujours en premier. Les opérateurs de requête sélectionnent et façonnent le résultat en fonction du type de source.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 La `From` clause spécifie `customers`la source de `cust`données, et une variable de *portée*, . La variable de plage est comme une variable d’itération en boucle, sauf que dans une expression de requête, aucune itération réelle ne se produit. Lorsque la requête est exécutée, `For Each` souvent en utilisant une boucle, la variable `customers`de plage sert de référence à chaque élément successif dans . Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement. Pour des exemples de requêtes écrites avec et sans dactylographie explicite, voir [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Pour plus d’informations `From` sur la façon d’utiliser la clause dans Visual Basic, voir [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Données filtantes (Où)  
 Probablement l’opération de requête la plus courante est l’application d’un filtre sous la forme d’une expression Boolean. La requête ne renvoie alors que les éléments pour lesquels l’expression est vraie. Une `Where` clause est utilisée pour effectuer le filtrage. Le filtre précise quels éléments de la source de données à inclure dans la séquence résultante. Dans l’exemple suivant, seuls les clients qui ont une adresse à Londres sont inclus.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Vous pouvez utiliser des `And` `Or` opérateurs logiques tels `Where` que et combiner des expressions de filtre dans une clause. Par exemple, pour ne retourner que les clients qui sont de Londres et dont le nom est Devon, utilisez le code suivant:  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 Pour renvoyer les clients de Londres ou de Paris, utilisez le code suivant :  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Pour plus d’informations `Where` sur la façon d’utiliser la clause dans Visual Basic, voir [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Données de commande (Ordre par)  
 Il est souvent pratique de trier les données retournées dans un ordre particulier. La `Order By` clause fera en sorte que les éléments de la séquence retournée seront triés sur un champ ou un champ spécifié. Par exemple, la requête suivante trie `Name` les résultats en fonction de la propriété. Parce `Name` que c’est une chaîne, les données retournées seront triées par ordre alphabétique, de A à Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `Order By...Descending`. La valeur `Ascending` par `Ascending` `Descending` défaut est lorsque ni ni est spécifié.  
  
 Pour plus d’informations `Order By` sur la façon d’utiliser la clause dans Visual Basic, voir [Ordre par clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Sélection des données (Sélectionner)  
 La `Select` clause spécifie le formulaire et le contenu des éléments retournés. Par exemple, vous pouvez spécifier `Customer` si vos `Customer` résultats seront composés d’objets complets, d’une seule propriété, d’un sous-ensemble de propriétés, d’une combinaison de propriétés provenant de diverses sources de données ou d’un nouveau type de résultat basé sur un calcul. Quand la clause `Select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*.  
  
 Pour récupérer une collection `Customer` composée d’objets complets, sélectionnez la variable de plage elle-même :  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Si `Customer` une instance est un grand objet qui a de nombreux champs, et `cust.Name`tout ce que vous voulez récupérer est le nom, vous pouvez sélectionner , comme indiqué dans l’exemple suivant. L’inférence de type local reconnaît que `Customer` cela modifie le type de résultat d’une collection d’objets à une collection de cordes.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Pour sélectionner plusieurs champs à partir de la source de données, vous avez deux choix :  
  
- Dans `Select` la clause, spécifiez les champs que vous souhaitez inclure dans le résultat. Le compilateur définira un type anonyme qui a ces champs comme ses propriétés. Pour plus d’informations, voir [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Étant donné que les éléments retournés dans l’exemple suivant sont des cas de type anonyme, vous ne pouvez pas vous référer au type par nom ailleurs dans votre code. Le nom désigné compilateur pour le type contient des caractères qui ne sont pas valides dans le code de base visuel normal. Dans l’exemple suivant, les éléments de la collection `londonCusts4` qui sont retournés par la requête sont des cas de type anonyme  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -ou-  
  
- Définissez un type nommé qui contient les champs particuliers que vous souhaitez inclure dans `Select` le résultat, et créez et initialisez des instances du type de la clause. Utilisez cette option uniquement si vous devez utiliser des résultats individuels en dehors de la collection dans laquelle ils sont retournés, ou si vous devez les passer comme paramètres dans les appels de méthode. Le type `londonCusts5` de dans l’exemple suivant est IEnumerable (De NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Pour plus d’informations `Select` sur la façon d’utiliser la clause dans Visual Basic, voir [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Rejoindre data (Join and Group Join)  
 Vous pouvez combiner plus d’une source de données dans la `From` clause de plusieurs façons. Par exemple, le code suivant utilise deux sources de données et combine implicitement les propriétés des deux dans le résultat. La requête sélectionne les étudiants dont les noms de famille commencent par une voyelle.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Vous pouvez exécuter ce code avec la liste des étudiants créés dans [Comment : Créer une liste d’objets](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Le `Join` mot clé `INNER JOIN` est équivalent à un SQL. Il combine deux collections basées sur des valeurs clés assorties entre les éléments des deux collections. La requête renvoie tout ou partie des éléments de collecte qui ont des valeurs clés correspondantes. Par exemple, le code suivant reproduit l’action de la jointure implicite précédente.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`combine des collections en une seule collection `LEFT JOIN` hiérarchique, tout comme un dans SQL. Pour plus d’informations, voir [Clause De jointure](../../../../visual-basic/language-reference/queries/join-clause.md) et [clause de jointure de groupe](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Groupement des données (Groupe par)  
 Vous pouvez `Group By` ajouter une clause pour regrouper les éléments dans un résultat de requête selon un ou plusieurs champs des éléments. Par exemple, le code suivant regroupe les élèves par année de classe.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Si vous exécutez ce code en utilisant la liste des étudiants créés dans [Comment : Créer une liste d’éléments,](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)la sortie de l’instruction `For Each` est :  
  
 Année: Junior  
  
 Michael Tucker  
  
 Hugo Garcia  
  
 Garcia, Debra  
  
 Lance Tucker  
  
 Année: Senior  
  
 Omelchenko, Svetlana  
  
 Michiko Osada  
  
 Fadi Fakhouri  
  
 Feng, Hanying  
  
 Terry Adams  
  
 Année: Freshman  
  
 Mortensen, Sven  
  
 César Garcia  
  
 La variation indiquée dans le code suivant commande les années de classe, puis commande les étudiants dans chaque année par nom de famille.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Pour plus `Group By`d’informations sur , voir [Groupe par clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic.IEnumerable%601>
- [Mise en route de LINQ dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
