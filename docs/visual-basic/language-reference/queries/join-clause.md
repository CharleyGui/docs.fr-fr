---
title: Join (clause)
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
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359772"
---
# <a name="join-clause-visual-basic"></a>Join, clause (Visual Basic)

Combine deux collections en une collection unique. L’opération de jointure est basée sur les clés correspondantes et utilise l' `Equals` opérateur.

## <a name="syntax"></a>Syntaxe

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Éléments

`element` Obligatoire. Variable de contrôle pour la collection qui est jointe.

`collection`  
Obligatoire. Collection à combiner avec la collection identifiée sur le côté gauche de l' `Join` opérateur. Une `Join` clause peut être imbriquée dans une autre `Join` clause ou dans une `Group Join` clause.

`joinClause`  
Facultatif. Une ou plusieurs `Join` clauses supplémentaires pour affiner la requête.

`groupJoinClause`  
Facultatif. Une ou plusieurs `Group Join` clauses supplémentaires pour affiner la requête.

`key1` `Equals` `key2`  
Obligatoire. Identifie les clés pour les collections qui sont jointes. Vous devez utiliser l' `Equals` opérateur pour comparer les clés des collections qui sont jointes. Vous pouvez combiner des conditions de jointure à l’aide de l' `And` opérateur pour identifier plusieurs clés. `key1`doit provenir de la collection sur le côté gauche de l' `Join` opérateur. `key2`doit provenir de la collection sur le côté droit de l' `Join` opérateur.

Les clés utilisées dans la condition de jointure peuvent être des expressions qui incluent plus d’un élément de la collection. Toutefois, chaque expression de clé peut contenir uniquement des éléments de sa collection respective.

## <a name="remarks"></a>Notes

La `Join` clause combine deux collections en fonction des valeurs de clé correspondantes des collections qui sont jointes. La collection résultante peut contenir n’importe quelle combinaison de valeurs de la collection identifiée sur le côté gauche de l' `Join` opérateur et la collection identifiée dans la `Join` clause. La requête retourne uniquement les résultats pour lesquels la condition spécifiée par l' `Equals` opérateur est remplie. Cela équivaut à une `INNER JOIN` dans SQL.

Vous pouvez utiliser plusieurs `Join` clauses dans une requête pour joindre deux collections ou plus dans une collection unique.

Vous pouvez effectuer une jointure implicite pour combiner des collections sans la `Join` clause. Pour ce faire, incluez plusieurs `In` clauses dans la `From` clause et spécifiez une `Where` clause qui identifie les clés que vous souhaitez utiliser pour la jointure.

Vous pouvez utiliser la `Group Join` clause pour combiner des collections dans une collection hiérarchique unique. C’est comme un `LEFT OUTER JOIN` dans SQL.

## <a name="example"></a>Exemple

L’exemple de code suivant effectue une jointure implicite pour combiner une liste de clients avec leurs commandes.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Exemple

L’exemple de code suivant joint deux collections à l’aide de la `Join` clause.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Cet exemple produira une sortie similaire à ce qui suit :

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Exemple

L’exemple de code suivant joint deux collections à l’aide de la `Join` clause avec deux colonnes clés.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

L’exemple produira une sortie similaire à ce qui suit :

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Voir aussi

- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Requêtes](index.md)
- [Clause SELECT](select-clause.md)
- [From, clause](from-clause.md)
- [Group Join (clause)](group-join-clause.md)
- [Clause WHERE](where-clause.md)
