---
title: Order By (clause)
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
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359746"
---
# <a name="order-by-clause-visual-basic"></a>Order By, clause (Visual Basic)
Spécifie l’ordre de tri des résultats d’une requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Éléments  
 `orderExp1`  
 Obligatoire. Un ou plusieurs champs du résultat de la requête actuelle qui identifient la façon dont les valeurs retournées doivent être triées. Les noms de champs doivent être séparés par des virgules (,). Vous pouvez identifier chaque champ comme trié dans l’ordre croissant ou décroissant à l’aide des `Ascending` `Descending` Mots clés ou. Si aucun `Ascending` `Descending` mot clé ou n’est spécifié, l’ordre de tri par défaut est croissant. Les champs d’ordre de tri sont prioritaires de gauche à droite.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la `Order By` clause pour trier les résultats d’une requête. La `Order By` clause peut uniquement trier un résultat en fonction de la variable de portée de l’étendue actuelle. Par exemple, la `Select` clause introduit une nouvelle étendue dans une expression de requête avec de nouvelles variables d’itération pour cette étendue. Les variables de plage définies avant une `Select` clause dans une requête ne sont pas disponibles après la `Select` clause. Par conséquent, si vous souhaitez classer vos résultats par un champ qui n’est pas disponible dans la `Select` clause, vous devez placer la `Order By` clause avant la `Select` clause. C’est le cas, par exemple, lorsque vous souhaitez trier votre requête par champs qui ne sont pas retournés dans le cadre du résultat.  
  
 L’ordre croissant et décroissant pour un champ est déterminé par l’implémentation de l' <xref:System.IComparable> interface pour le type de données du champ. Si le type de données n’implémente pas l' <xref:System.IComparable> interface, l’ordre de tri est ignoré.  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une `From` clause pour déclarer une variable `book` de portée pour la `books` collection. La `Order By` clause trie le résultat de la requête par prix dans l’ordre croissant (valeur par défaut). Les livres avec le même prix sont triés par titre dans l’ordre croissant. La `Select` clause sélectionne les `Title` `Price` Propriétés et comme valeurs retournées par la requête.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise la `Order By` clause pour trier le résultat de la requête par prix dans l’ordre décroissant. Les livres avec le même prix sont triés par titre dans l’ordre croissant.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Exemple  
 L’expression de requête suivante utilise une `Select` clause pour sélectionner le titre, le prix, la date de publication et l’auteur du livre. Il remplit ensuite les `Title` champs, `Price` , `PublishDate` et `Author` de la variable de portée pour la nouvelle portée. La `Order By` clause trie la nouvelle variable de portée par nom d’auteur, titre de livre, puis prix. Chaque colonne est triée dans l’ordre par défaut (croissant).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
