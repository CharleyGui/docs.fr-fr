---
title: Join, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: b0baca9f897a00b3c6c67699629477ff385d6ef7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353262"
---
# <a name="join-clause-visual-basic"></a>Join, clause (Visual Basic)

Combine deux collections en une collection unique. L’opération de jointure est basée sur les clés correspondantes et utilise l’opérateur `Equals`.

## <a name="syntax"></a>Syntaxe

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Composants

`element` (obligatoire). Variable de contrôle pour la collection qui est jointe.

`collection`  
Requis. Collection à combiner à la collection identifiée sur le côté gauche de l’opérateur `Join`. Une clause `Join` peut être imbriquée dans une autre clause `Join` ou dans une clause `Group Join`.

`joinClause`  
Ce paramètre est facultatif. Une ou plusieurs clauses de `Join` supplémentaires pour affiner la requête.

`groupJoinClause`  
Ce paramètre est facultatif. Une ou plusieurs clauses de `Group Join` supplémentaires pour affiner la requête.

`key1` `Equals` `key2`  
Requis. Identifie les clés pour les collections qui sont jointes. Vous devez utiliser l’opérateur `Equals` pour comparer les clés des collections qui sont jointes. Vous pouvez combiner des conditions de jointure à l’aide de l’opérateur `And` pour identifier plusieurs clés. `key1` doit provenir de la collection sur le côté gauche de l’opérateur `Join`. `key2` doit provenir de la collection sur le côté droit de l’opérateur `Join`.

Les clés utilisées dans la condition de jointure peuvent être des expressions qui incluent plus d’un élément de la collection. Toutefois, chaque expression de clé peut contenir uniquement des éléments de sa collection respective.

## <a name="remarks"></a>Notes

La clause `Join` combine deux collections en fonction des valeurs de clé correspondantes des collections qui sont jointes. La collection résultante peut contenir n’importe quelle combinaison de valeurs de la collection identifiée sur le côté gauche de l’opérateur `Join` et la collection identifiée dans la clause `Join`. La requête retourne uniquement les résultats pour lesquels la condition spécifiée par l’opérateur `Equals` est remplie. Cela équivaut à une `INNER JOIN` dans SQL.

Vous pouvez utiliser plusieurs clauses `Join` dans une requête pour joindre deux collections ou plus dans une collection unique.

Vous pouvez effectuer une jointure implicite pour combiner des collections sans la clause `Join`. Pour ce faire, incluez plusieurs clauses `In` dans votre clause `From` et spécifiez une clause `Where` qui identifie les clés que vous souhaitez utiliser pour la jointure.

Vous pouvez utiliser la clause `Group Join` pour combiner des collections dans une collection hiérarchique unique. C’est comme un `LEFT OUTER JOIN` dans SQL.

## <a name="example"></a>Exemple

L’exemple de code suivant effectue une jointure implicite pour combiner une liste de clients avec leurs commandes.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Exemple

L’exemple de code suivant joint deux collections à l’aide de la clause `Join`.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Cet exemple produira une sortie similaire à ce qui suit :

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Exemple

L’exemple de code suivant joint deux collections à l’aide de la clause `Join` avec deux colonnes clés.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

L’exemple produira une sortie similaire à ce qui suit :

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](../../../visual-basic/language-reference/queries/index.md)
- [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)
- [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)
- [Group Join (clause)](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
