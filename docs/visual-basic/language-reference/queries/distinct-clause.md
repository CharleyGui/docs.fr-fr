---
title: Distinct (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875273"
---
# <a name="distinct-clause-visual-basic"></a>Distinct, clause (Visual Basic)

Restreint les valeurs de la variable de portée actuelle pour éliminer les valeurs en double dans les clauses de requête suivantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Notes  

 Vous pouvez utiliser la `Distinct` clause pour retourner une liste d’éléments uniques. La `Distinct` clause force la requête à ignorer les résultats de la requête en double. La `Distinct` clause s’applique aux valeurs dupliquées pour tous les champs de retour spécifiés par la `Select` clause. Si aucune `Select` clause n’est spécifiée, la `Distinct` clause est appliquée à la variable de portée pour la requête identifiée dans la `From` clause. Si la variable de portée n’est pas un type immuable, la requête n’ignore un résultat de requête que si tous les membres du type correspondent à un résultat de requête existant.  
  
## <a name="example"></a>Exemple  

 L’expression de requête suivante joint une liste de clients et une liste de commandes client. La `Distinct` clause est incluse pour retourner une liste de noms de clients uniques et de dates de commande.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [From, clause](from-clause.md)
- [Clause SELECT](select-clause.md)
- [Clause WHERE](where-clause.md)
