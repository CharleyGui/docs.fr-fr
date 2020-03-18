---
title: 'Comment : utiliser des blocs finally'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708830"
---
# <a name="how-to-use-finally-blocks"></a>Guide pratique pour utiliser des blocs finally

Quand une exception se produit, l’exécution s’arrête et le contrôle est donné au gestionnaire d’exceptions approprié. Cela signifie souvent que les lignes de code qui doivent être exécutées sont ignorées. Un nettoyage des ressources, comme la fermeture d’un fichier, doit être effectué même si une exception est levée. Pour ce faire, vous pouvez utiliser un bloc `finally`. Un bloc `finally` s’exécute toujours, qu’une exception soit levée ou non.

L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.ArgumentOutOfRangeException>. La méthode `Main` crée deux tableaux et tente de copier l’un dans l’autre. Cette action génère une exception <xref:System.ArgumentOutOfRangeException> et l’erreur est écrite dans la console. Le bloc `finally` s’exécute indépendamment du résultat de l’action de copie.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
