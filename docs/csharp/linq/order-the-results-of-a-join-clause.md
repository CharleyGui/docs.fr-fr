---
title: Classer les résultats d'une clause join (LINQ en C#)
description: Découvrez comment classer les résultats d'une clause join LINQ en C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659863"
---
# <a name="order-the-results-of-a-join-clause"></a>Classer les résultats d’une clause join

Cet exemple montre comment classer les résultats d’une opération de jointure. Notez que le classement est effectué après la jointure. Vous pouvez utiliser une clause `orderby` avec une ou plusieurs séquences sources avant la jointure, mais cette pratique est généralement déconseillée. Certains fournisseurs LINQ ne conservent pas ce classement après la jointure.

## <a name="example"></a> Exemple

Cette requête crée une jointure groupée, puis trie les groupes en fonction de l’élément de catégorie, qui est encore dans la portée. À l’intérieur de l’initialiseur de type anonyme, une sous-requête classe tous les éléments correspondants de la séquence de produits.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Voir aussi

- [Requête intégrée linguistique (LINQ)](index.md)
- [orderby, clause](../language-reference/keywords/orderby-clause.md)
- [clause d’adhésion](../language-reference/keywords/join-clause.md)
