---
title: Order By, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: a7104e3dd82ff2dde2911861ce98a7367faf3b25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350417"
---
# <a name="order-by-clause-visual-basic"></a>Order By, clause (Visual Basic)
Spécifie l’ordre de tri des résultats d’une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Composants  
 `orderExp1`  
 Requis. Un ou plusieurs champs du résultat de la requête actuelle qui identifient la façon dont les valeurs retournées doivent être triées. Les noms de champs doivent être séparés par des virgules (,). Vous pouvez identifier chaque champ comme trié dans l’ordre croissant ou décroissant à l’aide des mots clés `Ascending` ou `Descending`. Si aucun `Ascending` ou `Descending` mot clé n’est spécifié, l’ordre de tri par défaut est croissant. Les champs d’ordre de tri sont prioritaires de gauche à droite.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la clause `Order By` pour trier les résultats d’une requête. La clause `Order By` peut uniquement trier un résultat en fonction de la variable de portée de l’étendue actuelle. Par exemple, la clause `Select` introduit une nouvelle étendue dans une expression de requête avec de nouvelles variables d’itération pour cette étendue. Les variables de plage définies avant une clause `Select` dans une requête ne sont pas disponibles après la clause `Select`. Par conséquent, si vous souhaitez classer vos résultats par un champ qui n’est pas disponible dans la clause `Select`, vous devez placer la clause `Order By` avant la clause `Select`. C’est le cas, par exemple, lorsque vous souhaitez trier votre requête par champs qui ne sont pas retournés dans le cadre du résultat.  
  
 L’ordre croissant et décroissant pour un champ est déterminé par l’implémentation de l’interface <xref:System.IComparable> pour le type de données du champ. Si le type de données n’implémente pas l’interface <xref:System.IComparable>, l’ordre de tri est ignoré.  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `book` pour la collection de `books`. La clause `Order By` trie le résultat de la requête par prix dans l’ordre croissant (valeur par défaut). Les livres avec le même prix sont triés par titre dans l’ordre croissant. La clause `Select` sélectionne les propriétés `Title` et `Price` comme valeurs retournées par la requête.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise la clause `Order By` pour trier le résultat de la requête par prix dans l’ordre décroissant. Les livres avec le même prix sont triés par titre dans l’ordre croissant.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une clause `Select` pour sélectionner le titre, le prix, la date de publication et l’auteur du livre. Il remplit ensuite les champs `Title`, `Price`, `PublishDate`et `Author` de la variable de portée pour la nouvelle portée. La clause `Order By` trie la nouvelle variable de portée par nom d’auteur, titre de livre, puis prix. Chaque colonne est triée dans l’ordre par défaut (croissant).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
