---
title: 'Comment : utiliser des exceptions spécifiques dans un bloc catch'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: bf4813e950b034cb807abebfe016c1e34487d594
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828021"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Utiliser des exceptions spécifiques dans un bloc Catch

En général, il est conseillé en programmation d’intercepter un type d’exception spécifique au lieu d’utiliser une instruction `catch` de base.

Quand une exception se produit, elle remonte la pile et chaque bloc catch a la possibilité de la gérer. L’ordre des instructions catch est important. Placez les blocs catch ciblés sur des exceptions spécifiques avant un bloc catch d’exceptions générales, sinon le compilateur peut générer une erreur. Le bloc catch approprié est déterminé en mettant en correspondance le type de l’exception avec le nom de l’exception spécifiée dans le bloc catch. S’il n’existe aucun bloc catch spécifique, l’exception est interceptée par un bloc catch général, le cas échéant.

L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.InvalidCastException>. L’exemple crée une classe appelée `Employee` avec une propriété unique, le niveau de l’employé (`Emlevel`). Une méthode `PromoteEmployee` prend un objet et incrémente le niveau de l’employé. Une exception <xref:System.InvalidCastException> se produit quand une instance <xref:System.DateTime> est passée à la méthode `PromoteEmployee`.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
