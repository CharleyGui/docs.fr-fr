---
title: Group By (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: b60f6759ada845d8eab048bceb1e47f9546ee7d0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869949"
---
# <a name="group-by-clause-visual-basic"></a>Group By, clause (Visual Basic)

Regroupe les éléments d'un résultat de requête. Peut aussi être utilisée pour appliquer des fonctions d’agrégation à chaque groupe. L’opération de regroupement est basée sur une ou plusieurs clés.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Éléments  
  
- `listField1`, `listField2`  
  
     Optionnel. Un ou plusieurs champs de la ou des variables de requête qui identifient explicitement les champs à inclure dans le résultat groupé. Si aucun champ n’est spécifié, tous les champs de la ou des variables de requête sont inclus dans le résultat groupé.  
  
- `keyExp1`  
  
     Obligatoire. Expression qui identifie la clé à utiliser pour déterminer les groupes d’éléments. Vous pouvez spécifier plusieurs clés pour spécifier une clé composite.  
  
- `keyExp2`  
  
     Optionnel. Une ou plusieurs clés supplémentaires combinées à `keyExp1` pour créer une clé composite.  
  
- `aggregateList`  
  
     Obligatoire. Une ou plusieurs expressions qui identifient la façon dont les groupes sont agrégés. Pour identifier un nom de membre pour les résultats groupés, utilisez le mot clé `Group` , qui peut prendre l’une des formes suivantes :  
  
    ```vb  
    Into Group  
    ```  
  
     - ou -  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     Vous pouvez aussi inclure des fonctions d’agrégation à appliquer au groupe.  
  
## <a name="remarks"></a>Notes  

 Vous pouvez utiliser la clause `Group By` pour décomposer les résultats d’une requête en groupes. Le regroupement est basé sur une clé ou une clé composite constituée de plusieurs clés. Les éléments associés à des valeurs de clé correspondantes sont inclus dans le même groupe.  
  
 Utilisez le paramètre `aggregateList` de la clause `Into` et le mot clé `Group` pour identifier le nom de membre servant à référencer le groupe. Vous pouvez aussi inclure des fonctions d’agrégation dans la clause `Into` pour calculer les valeurs des éléments groupés. Pour obtenir la liste des fonctions d’agrégation standard, consultez [Aggregate Clause](aggregate-clause.md).  
  
## <a name="example"></a>Exemple  

 L’exemple de code suivant regroupe une liste de clients en fonction de leur emplacement (pays/région) et fournit le nombre de clients dans chaque groupe. Les résultats sont triés par nom de pays/région. Les résultats groupés sont organisés par nom de ville.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Clause ORDER BY](order-by-clause.md)
- [Aggregate Clause](aggregate-clause.md)
- [Group Join (clause)](group-join-clause.md)
