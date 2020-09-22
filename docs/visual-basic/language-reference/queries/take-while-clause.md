---
title: Take While (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 632e9e2195f21a3aa1d1ffd28e9838905c471156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869656"
---
# <a name="take-while-clause-visual-basic"></a>Take While, clause (Visual Basic)

Inclut les éléments d’une collection tant qu’une condition spécifiée a la valeur `true` et ignore les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`expression`|Obligatoire. Expression qui représente une condition pour laquelle tester des éléments. L’expression doit retourner une `Boolean` valeur ou un équivalent fonctionnel, tel qu’un `Integer` à évaluer en tant que `Boolean` .|  
  
## <a name="remarks"></a>Notes  

 La `Take While` clause comprend des éléments à partir du début d’un résultat de requête jusqu’à ce que le `expression` retourne fourni `false` . Une fois le `expression` retourné `false` , la requête contourne tous les éléments restants. `expression`Est ignoré pour les résultats restants.  
  
 La clause `Take While` est différente de la clause `Where` dans la `Where` mesure où la clause peut être utilisée pour inclure tous les éléments d’une requête qui remplissent une condition particulière. La `Take While` clause comprend uniquement des éléments jusqu’à la première fois que la condition n’est pas satisfaite. La `Take While` clause est particulièrement utile lorsque vous travaillez avec un résultat de requête ordonné.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant utilise la `Take While` clause pour récupérer les résultats jusqu’à ce que le premier client sans ordre soit trouvé.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Take (clause)](take-clause.md)
- [SkipWhile (clause)](skip-while-clause.md)
- [Clause WHERE](where-clause.md)
