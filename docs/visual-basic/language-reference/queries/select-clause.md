---
title: Select, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 5ebb813229d5d517b369036c69b2d23c8ee1c9f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350406"
---
# <a name="select-clause-visual-basic"></a>Select, clause (Visual Basic)
Définit le résultat d’une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Composants  
 `var1`  
 Ce paramètre est facultatif. Alias qui peut être utilisé pour référencer les résultats de l’expression de colonne.  
  
 `fieldName1`  
 Requis. Nom du champ à retourner dans le résultat de la requête.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la clause `Select` pour définir les résultats à retourner à partir d’une requête. Cela vous permet de définir les membres d’un nouveau type anonyme créé par une requête, ou de cibler les membres d’un type nommé qui est retourné par une requête. La clause `Select` n’est pas requise pour une requête. Si aucune clause `Select` n’est spécifiée, la requête retourne un type en fonction de tous les membres des variables de plage identifiées pour l’étendue actuelle. Pour plus d’informations, consultez [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Quand une requête crée un type nommé, elle retourne un résultat de type <xref:System.Collections.Generic.IEnumerable%601> où `T` est le type créé.  
  
 La clause `Select` peut faire référence à toutes les variables dans l’étendue actuelle. Cela comprend les variables de plage identifiées dans la clause `From` (ou les clauses `From`). Elle comprend également les nouvelles variables créées avec un alias par les clauses `Aggregate`, `Let`, `Group By`ou `Group Join`, ou les variables d’une clause `Select` précédente dans l’expression de requête. La clause `Select` peut également inclure des valeurs statiques. Par exemple, l’exemple de code suivant affiche une expression de requête dans laquelle la clause `Select` définit le résultat de la requête en tant que nouveau type anonyme avec quatre membres : `ProductName`, `Price`, `Discount`et `DiscountedPrice`. Les valeurs des membres `ProductName` et `Price` sont extraites de la variable de plage de produits définie dans la clause `From`. La valeur du membre `DiscountedPrice` est calculée dans la clause `Let`. Le membre `Discount` est une valeur statique.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 La clause `Select` introduit un nouvel ensemble de variables de plage pour les clauses de requête suivantes, et les variables de plage précédentes ne sont plus dans la portée. La dernière clause `Select` dans une expression de requête détermine la valeur de retour de la requête. Par exemple, la requête ci-dessous retourne le nom de la société et l’ID de commande pour chaque commande client dont le total dépasse 500. La première clause `Select` identifie les variables de plage pour la clause `Where` et la deuxième clause `Select`. La deuxième clause `Select` identifie les valeurs retournées par la requête sous la forme d’un nouveau type anonyme.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Si la clause `Select` identifie un élément unique à retourner, l’expression de requête retourne une collection du type de cet élément unique. Si la clause `Select` identifie plusieurs éléments à retourner, l’expression de requête retourne une collection d’un nouveau type anonyme, en fonction des éléments sélectionnés. Par exemple, les deux requêtes suivantes retournent des collections de deux types différents en fonction de la clause `Select`. La première requête retourne une collection de noms de société sous forme de chaînes. La deuxième requête retourne une collection d’objets `Customer` renseignés avec les noms et les informations d’adresse de la société.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `cust` pour la collection de `customers`. La clause `Select` sélectionne la valeur du nom et de l’ID du client et remplit les colonnes `CompanyName` et `CustomerID` de la nouvelle variable de portée. L’instruction `For Each` effectue une boucle sur chaque objet retourné et affiche les colonnes `CompanyName` et `CustomerID` pour chaque enregistrement.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
