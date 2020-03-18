---
title: Guide pratique pour utiliser le bloc try/catch pour intercepter des exceptions
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
ms.openlocfilehash: 5a9218d394b76e897f4263708a10f1bc895ad4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708464"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Guide pratique pour utiliser le bloc try/catch pour intercepter des exceptions

Placez les instructions de code qui peuvent déclencher ou lever une exception dans un bloc `try` et placez les instructions utilisées pour gérer l’exception ou les exceptions dans un ou plusieurs blocs `catch` sous le bloc `try`. Chaque bloc `catch` inclut le type d’exception et peut contenir des instructions supplémentaires nécessaires pour gérer ce type d’exception.

Dans l’exemple suivant, un <xref:System.IO.StreamReader> ouvre un fichier appelé *data.txt* et récupère une ligne de ce fichier. Étant donné que le code peut lever une des trois exceptions, il est placé dans un bloc `try`. Trois blocs `catch` interceptent les exceptions et les gèrent en affichant les résultats dans la console.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Le Common Language Runtime (CLR) intercepte les exceptions non gérées par les blocs `catch`. Si une exception est interceptée par le CLR, il peut se produire l’un des résultats suivants selon la configuration du CLR :

- Une boîte de dialogue **Débogage** s’affiche.
- Le programme s’arrête et une boîte de dialogue d’information sur l’exception s’affiche.
- Une erreur s’affiche dans le [flux de sortie d’erreur standard](xref:System.Console.Error).

> [!NOTE]
> La plupart du code peut lever une exception, et quelques exceptions comme <xref:System.OutOfMemoryException> peuvent être levées par le CLR lui-même à tout moment. L’utilisation d’applications n’est pas obligatoire pour traiter ces exceptions, mais envisagez cette possibilité quand vous écrivez des bibliothèques destinées à l’usage d’autres utilisateurs. Si vous souhaitez des conseils sur la définition de code dans un bloc `try`, consultez [Bonnes pratiques pour les exceptions](best-practices-for-exceptions.md).

## <a name="see-also"></a>Voir aussi

- [Exceptions](index.md)
- [Gestion des erreurs E/S dans .NET](../io/handling-io-errors.md)
