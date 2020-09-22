---
title: Select (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: d96423efbee075a7ad257df72471c71e38e09b63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875748"
---
# <a name="select-clause-visual-basic"></a>Select, clause (Visual Basic)

Définit le résultat d’une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Éléments  

 `var1`  
 Optionnel. Alias qui peut être utilisé pour référencer les résultats de l’expression de colonne.  
  
 `fieldName1`  
 Obligatoire. Nom du champ à retourner dans le résultat de la requête.  
  
## <a name="remarks"></a>Notes  

 Vous pouvez utiliser la `Select` clause pour définir les résultats à retourner à partir d’une requête. Cela vous permet de définir les membres d’un nouveau type anonyme créé par une requête, ou de cibler les membres d’un type nommé qui est retourné par une requête. La `Select` clause n’est pas requise pour une requête. Si aucune `Select` clause n’est spécifiée, la requête retourne un type en fonction de tous les membres des variables de plage identifiées pour l’étendue actuelle. Pour plus d’informations, consultez [types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md). Quand une requête crée un type nommé, elle retourne un résultat de type <xref:System.Collections.Generic.IEnumerable%601> où `T` est le type créé.  
  
 La `Select` clause peut faire référence à toutes les variables dans l’étendue actuelle. Cela comprend les variables de plage identifiées dans la `From` clause ( `From` clauses or). Elle comprend également les nouvelles variables créées avec un alias par les `Aggregate` `Let` `Group By` clauses,, ou `Group Join` , ou les variables d’une `Select` clause précédente dans l’expression de requête. La `Select` clause peut également inclure des valeurs statiques. Par exemple, l’exemple de code suivant affiche une expression de requête dans laquelle la `Select` clause définit le résultat de la requête en tant que nouveau type anonyme avec quatre membres : `ProductName` , `Price` , `Discount` et `DiscountedPrice` . Les `ProductName` `Price` valeurs de membre et sont extraites de la variable de plage de produits définie dans la `From` clause. La `DiscountedPrice` valeur de membre est calculée dans la `Let` clause. Le `Discount` membre est une valeur statique.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 La `Select` clause introduit un nouvel ensemble de variables de plage pour les clauses de requête suivantes, et les variables de plage précédentes ne sont plus dans la portée. La dernière `Select` clause dans une expression de requête détermine la valeur de retour de la requête. Par exemple, la requête ci-dessous retourne le nom de la société et l’ID de commande pour chaque commande client dont le total dépasse 500. La première `Select` clause identifie les variables de plage de la `Where` clause et de la deuxième `Select` clause. La deuxième `Select` clause identifie les valeurs retournées par la requête sous la forme d’un nouveau type anonyme.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Si la `Select` clause identifie un seul élément à retourner, l’expression de requête retourne une collection du type de cet élément unique. Si la `Select` clause identifie plusieurs éléments à retourner, l’expression de requête retourne une collection d’un nouveau type anonyme, en fonction des éléments sélectionnés. Par exemple, les deux requêtes suivantes retournent des collections de deux types différents en fonction de la `Select` clause. La première requête retourne une collection de noms de société sous forme de chaînes. La deuxième requête retourne une collection d' `Customer` objets remplis avec les noms et les informations d’adresse de la société.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Exemple  

 L’expression de requête suivante utilise une `From` clause pour déclarer une variable `cust` de portée pour la `customers` collection. La `Select` clause sélectionne la valeur du nom et de l’ID du client et remplit les `CompanyName` `CustomerID` colonnes et de la nouvelle variable de portée. L' `For Each` instruction effectue une boucle sur chaque objet retourné et affiche les `CompanyName` `CustomerID` colonnes et pour chaque enregistrement.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [From, clause](from-clause.md)
- [Clause WHERE](where-clause.md)
- [Clause ORDER BY](order-by-clause.md)
- [Types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
