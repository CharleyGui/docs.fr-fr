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
ms.openlocfilehash: e9a646d60bb22507f4c6bcbcdf9222fd0ed18f02
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345751"
---
# <a name="basic-query-operations-visual-basic"></a>Opérations de requête de base (Visual Basic)
Cette rubrique fournit une brève introduction à [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions dans Visual Basic, et à certains types d’opérations classiques que vous effectuez dans une requête. Pour plus d’informations, consultez les rubriques suivantes :  
  
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Requêtes](../../../../visual-basic/language-reference/queries/index.md)  
  
 [Procédure pas à pas : écriture de requêtes dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>Spécification de la source de données (à partir de)  
 Dans une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], la première étape consiste à spécifier la source de données que vous souhaitez interroger. Par conséquent, la clause `From` dans une requête est toujours la première. Les opérateurs de requête sélectionnent et déforment le résultat en fonction du type de la source.  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 La clause `From` spécifie la source de données, `customers`et une *variable de portée*, `cust`. La variable de portée est semblable à une variable d’itération de boucle, sauf que dans une expression de requête, aucune itération réelle n’est effectuée. Lorsque la requête est exécutée, souvent à l’aide d’une `For Each` boucle, la variable de portée sert de référence à chaque élément successif dans `customers`. Comme le compilateur déduit le type de `cust`, vous n’avez pas à le spécifier explicitement. Pour obtenir des exemples de requêtes écrites avec et sans typage explicite, consultez [relations de types dans les opérations de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Pour plus d’informations sur l’utilisation de la clause `From` dans Visual Basic, consultez [from, clause](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## <a name="filtering-data-where"></a>Filtrage des données (où)  
 L’opération de requête la plus courante est probablement l’application d’un filtre sous la forme d’une expression booléenne. La requête retourne alors uniquement les éléments pour lesquels l’expression a la valeur true. Une clause `Where` est utilisée pour effectuer le filtrage. Le filtre spécifie les éléments de la source de données à inclure dans la séquence résultante. Dans l’exemple suivant, seuls les clients qui ont une adresse à Londres sont inclus.  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 Vous pouvez utiliser des opérateurs logiques tels que `And` et `Or` pour combiner des expressions de filtre dans une clause `Where`. Par exemple, pour retourner uniquement les clients de Londres et dont le nom est Devon, utilisez le code suivant :  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Pour retourner les clients de Londres ou Paris, utilisez le code suivant :  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Pour plus d’informations sur l’utilisation de la clause `Where` dans Visual Basic, consultez [clause WHERE](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## <a name="ordering-data-order-by"></a>Tri des données (Order By)  
 Il est souvent pratique de trier les données retournées dans un ordre particulier. La clause `Order By` entraîne le tri des éléments de la séquence retournée sur un champ ou des champs spécifiés. Par exemple, la requête suivante trie les résultats en fonction de la propriété `Name`. Étant donné que `Name` est une chaîne, les données retournées sont triées par ordre alphabétique, de A à Z.  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 Pour trier les résultats dans l’ordre inverse, de Z à A, utilisez la clause `Order By...Descending`. La valeur par défaut est `Ascending` lorsque ni `Ascending` ni `Descending` n’est spécifié.  
  
 Pour plus d’informations sur l’utilisation de la clause `Order By` dans Visual Basic, consultez [clause ORDER BY](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## <a name="selecting-data-select"></a>Sélection des données (Select)  
 La clause `Select` spécifie la forme et le contenu des éléments retournés. Par exemple, vous pouvez spécifier si vos résultats seront composés d’objets `Customer` complets, d’une seule `Customer` propriété, d’un sous-ensemble de propriétés, d’une combinaison de propriétés provenant de diverses sources de données ou d’un nouveau type de résultat basé sur un calcul. Quand la clause `Select` produit autre chose qu’une copie de l’élément source, l’opération est appelée *projection*.  
  
 Pour récupérer une collection qui se compose d’objets `Customer` complets, sélectionnez la variable de portée proprement dite :  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 Si une instance de `Customer` est un objet volumineux qui contient de nombreux champs, et que vous souhaitez récupérer le nom, vous pouvez sélectionner `cust.Name`, comme indiqué dans l’exemple suivant. L’inférence de type local reconnaît que ce modifie le type de résultat d’une collection d’objets `Customer` en une collection de chaînes.  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 Pour sélectionner plusieurs champs de la source de données, vous avez deux possibilités :  
  
- Dans la clause `Select`, spécifiez les champs que vous souhaitez inclure dans le résultat. Le compilateur définit un type anonyme dont les propriétés sont les champs. Pour plus d’informations, consultez [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Étant donné que les éléments retournés dans l’exemple suivant sont des instances d’un type anonyme, vous ne pouvez pas faire référence au type par un autre nom dans votre code. Le nom désigné par le compilateur pour le type contient des caractères qui ne sont pas valides dans le code Visual Basic normal. Dans l’exemple suivant, les éléments de la collection qui est retournée par la requête dans `londonCusts4` sont des instances d’un type anonyme  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     -ou-  
  
- Définissez un type nommé qui contient les champs particuliers que vous souhaitez inclure dans le résultat, et créez et initialisez des instances du type dans la clause `Select`. Utilisez cette option uniquement si vous devez utiliser des résultats individuels en dehors de la collection dans laquelle ils sont retournés, ou si vous devez les passer en tant que paramètres dans les appels de méthode. Le type de `londonCusts5` dans l’exemple suivant est IEnumerable (of NamePhone).  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Pour plus d’informations sur l’utilisation de la clause `Select` dans Visual Basic, consultez [Select, clause](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## <a name="joining-data-join-and-group-join"></a>Jointure de données (jointure et jointure groupée)  
 Vous pouvez combiner plusieurs sources de données dans la clause `From` de plusieurs façons. Par exemple, le code suivant utilise deux sources de données et combine implicitement les propriétés des deux dans le résultat. La requête sélectionne les élèves dont les noms commencent par une voyelle.  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> Vous pouvez exécuter ce code avec la liste des élèves créée dans [How to : Create a list of items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Le mot clé `Join` est équivalent à un `INNER JOIN` dans SQL. Il combine deux collections en fonction des valeurs de clé correspondantes entre les éléments des deux collections. La requête retourne tout ou partie des éléments de la collection qui ont des valeurs de clé correspondantes. Par exemple, le code suivant duplique l’action de la jointure implicite précédente.  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` combine des collections dans une collection hiérarchique unique, tout comme une `LEFT JOIN` dans SQL. Pour plus d’informations, consultez [clause join](../../../../visual-basic/language-reference/queries/join-clause.md) et [clause Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## <a name="grouping-data-group-by"></a>Regroupement de données (Group by)  
 Vous pouvez ajouter une clause `Group By` pour regrouper les éléments d’un résultat de requête en fonction d’un ou de plusieurs champs des éléments. Par exemple, le code suivant regroupe les étudiants par année de classe.  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 Si vous exécutez ce code à l’aide de la liste des élèves créée dans [How to : Create a list of items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), la sortie de l’instruction `For Each` est la suivante :  
  
 Année : Junior  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Marie  
  
 Tucker, lance  
  
 Année : Senior  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Année : actualité  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 La variation indiquée dans le code suivant trie les années de la classe, puis classe les étudiants au cours de chaque année par nom.  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 Pour plus d’informations sur `Group By`, consultez [clause Group by](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic.IEnumerable%601>
- [Bien démarrer avec LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
