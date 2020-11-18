---
title: 'Comment : utiliser des blocs finally'
ms.date: 03/30/2017
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
ms.openlocfilehash: 8bc36ce9a755762bb5159a27f9ef5699b2992f0e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828034"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="e9510-102">Guide pratique pour utiliser des blocs finally</span><span class="sxs-lookup"><span data-stu-id="e9510-102">How to use finally blocks</span></span>

<span data-ttu-id="e9510-103">Quand une exception se produit, l’exécution s’arrête et le contrôle est donné au gestionnaire d’exceptions approprié.</span><span class="sxs-lookup"><span data-stu-id="e9510-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="e9510-104">Cela signifie souvent que les lignes de code qui doivent être exécutées sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="e9510-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="e9510-105">Un nettoyage des ressources, comme la fermeture d’un fichier, doit être effectué même si une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="e9510-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="e9510-106">Pour ce faire, vous pouvez utiliser un bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="e9510-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="e9510-107">Un bloc `finally` s’exécute toujours, qu’une exception soit levée ou non.</span><span class="sxs-lookup"><span data-stu-id="e9510-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="e9510-108">L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="e9510-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="e9510-109">La méthode `Main` crée deux tableaux et tente de copier l’un dans l’autre.</span><span class="sxs-lookup"><span data-stu-id="e9510-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="e9510-110">Cette action génère une exception <xref:System.ArgumentOutOfRangeException> et l’erreur est écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="e9510-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="e9510-111">Le bloc `finally` s’exécute indépendamment du résultat de l’action de copie.</span><span class="sxs-lookup"><span data-stu-id="e9510-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="e9510-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9510-112">See also</span></span>

- [<span data-ttu-id="e9510-113">Exceptions</span><span class="sxs-lookup"><span data-stu-id="e9510-113">Exceptions</span></span>](index.md)
