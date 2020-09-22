---
title: SkipWhile (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: af722f7aee021f244b411cdc61619b7de3c20607
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866226"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While, clause (Visual Basic)

Ignore les éléments d’une collection tant qu’une condition spécifiée a la valeur `true`, puis retourne les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`expression`|Obligatoire. Expression qui représente une condition pour laquelle tester des éléments. L’expression doit retourner une `Boolean` valeur ou un équivalent fonctionnel, tel qu’un `Integer` à évaluer en tant que `Boolean` .|  
  
## <a name="remarks"></a>Notes  

 La `Skip While` clause ignore les éléments à partir du début d’un résultat de requête jusqu’à ce que le fourni soit `expression` retourné `false` . Une fois que `expression` retourne `false` , la requête retourne tous les éléments restants. `expression`Est ignoré pour les résultats restants.  
  
 La clause `Skip While` est différente de la clause `Where` dans la `Where` mesure où la clause peut être utilisée pour exclure tous les éléments d’une requête qui ne respectent pas une condition particulière. La `Skip While` clause exclut les éléments uniquement jusqu’à la première fois que la condition n’est pas satisfaite. La `Skip While` clause est particulièrement utile lorsque vous travaillez avec un résultat de requête ordonné.  
  
 Vous pouvez ignorer un nombre spécifique de résultats à partir du début d’un résultat de requête à l’aide de la `Skip` clause.  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant utilise la `Skip While` clause pour ignorer les résultats jusqu’à ce que le premier client du États-Unis soit trouvé.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Skip (clause)](skip-clause.md)
- [Take While (clause)](take-while-clause.md)
- [Clause WHERE](where-clause.md)
