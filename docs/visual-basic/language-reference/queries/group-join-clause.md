---
title: Group Join (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 7916e51293c06016b2581b7109df3f0a599404ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359830"
---
# <a name="group-join-clause-visual-basic"></a>Group Join, clause (Visual Basic)
Combine deux collections en une collection hiérarchique unique. L’opération de jointure est basée sur les clés correspondantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. Variable de contrôle pour la collection qui est jointe.|  
|`type`|Facultatif. Type d'élément `element`. Si aucun `type` n’est spécifié, le type de `element` est déduit à partir de `collection` .|  
|`collection`|Obligatoire. Collection à combiner avec la collection qui se trouve sur le côté gauche de l' `Group Join` opérateur. Une `Group Join` clause peut être imbriquée dans une `Join` clause ou dans une autre `Group Join` clause.|  
|`key1` `Equals` `key2`|Obligatoire. Identifie les clés pour les collections qui sont jointes. Vous devez utiliser l' `Equals` opérateur pour comparer les clés des collections qui sont jointes. Vous pouvez combiner des conditions de jointure à l’aide de l' `And` opérateur pour identifier plusieurs clés. Le `key1` paramètre doit provenir de la collection sur le côté gauche de l' `Join` opérateur. Le `key2` paramètre doit provenir de la collection située à droite de l' `Join` opérateur.<br /><br /> Les clés utilisées dans la condition de jointure peuvent être des expressions qui incluent plus d’un élément de la collection. Toutefois, chaque expression de clé peut contenir uniquement des éléments de sa collection respective.|  
|`expressionList`|Obligatoire. Une ou plusieurs expressions qui identifient la façon dont les groupes d’éléments de la collection sont agrégés. Pour identifier un nom de membre pour les résultats groupés, utilisez le `Group` mot clé ( `<alias> = Group` ). Vous pouvez aussi inclure des fonctions d’agrégation à appliquer au groupe.|  
  
## <a name="remarks"></a>Notes  
 La `Group Join` clause combine deux collections en fonction des valeurs de clé correspondantes des collections qui sont jointes. La collection résultante peut contenir un membre qui fait référence à une collection d’éléments de la deuxième collection qui correspondent à la valeur de clé de la première collection. Vous pouvez également spécifier des fonctions d’agrégation à appliquer aux éléments groupés à partir de la deuxième collection. Pour plus d’informations sur les fonctions d’agrégation, consultez [Aggregate, clause](aggregate-clause.md).  
  
 Prenons l’exemple d’une collection de gestionnaires et d’un regroupement d’employés. Les éléments des deux collections ont une propriété ManagerID qui identifie les employés qui sont en rapport avec un gestionnaire spécifique. Les résultats d’une opération de jointure contiennent un résultat pour chaque responsable et chaque employé avec une valeur ManagerID correspondante. Les résultats d’une `Group Join` opération contiennent la liste complète des gestionnaires. Chaque résultat de responsable aurait un membre qui référençait la liste des employés qui correspondaient à un gestionnaire spécifique.  
  
 La collection qui résulte d’une `Group Join` opération peut contenir n’importe quelle combinaison de valeurs de la collection identifiée dans la `From` clause et les expressions identifiées dans la `Into` clause de la clause `Group Join` . Pour plus d’informations sur les expressions valides pour la `Into` clause, consultez [Aggregate, clause](aggregate-clause.md).  
  
 Une `Group Join` opération renverra tous les résultats de la collection identifiée sur le côté gauche de l' `Group Join` opérateur. Cela est vrai même s’il n’y a aucune correspondance dans la collection jointe. C’est comme un `LEFT OUTER JOIN` dans SQL.  
  
 Vous pouvez utiliser la `Join` clause pour combiner des collections dans une collection unique. Cela équivaut à une `INNER JOIN` dans SQL.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant joint deux collections à l’aide de la `Group Join` clause.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Join (clause)](join-clause.md)
- [Clause WHERE](where-clause.md)
- [Group by, clause](group-by-clause.md)
