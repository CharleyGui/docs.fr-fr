---
title: Débbuggers gérés - .NET Core
description: Un aperçu du Visual Studio et Visual Studio Code géré débrilleurs.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715566"
---
# <a name="net-core-managed-debuggers"></a>.NET Core a géré les débbuggeurs

Les débbuggeurs permettent aux programmes d’être mis en pause ou exécutés étape par étape. Une fois mis en pause, l’état actuel du processus peut être consulté. En franchiant les sections clés, vous obtenez une compréhension de votre code et pourquoi il produit le résultat qu’il fait.

Microsoft fournit des débbuggers pour le code géré dans **Visual Studio** et Visual **Studio Code**.

## <a name="visual-studio-managed-debugger"></a>Visual Studio géré débbugger

**Visual Studio** est un environnement de développement intégré avec le débbuggeur le plus complet disponible. Visual Studio est un excellent choix pour les développeurs travaillant sur Windows.

- [Tutorial - Débogage d’une application .NET Core sur Windows avec Visual Studio](../tutorials/debugging-with-visual-studio.md)

Bien que Visual Studio soit une application Windows, il peut toujours être utilisé pour déboiffer les applications Linux et macOS à distance.

- [Déboguer une application .NET Core sur Linux/OSX avec Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 Le débogage ASP.NET les applications Core nécessitent des instructions légèrement différentes.

- [Debug ASP.NET applications De Core dans Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Code de studio visuel géré débrisonneur

**Visual Studio Code** est un éditeur de code multiplateforme léger. Il utilise la même implémentation .NET Core debugger que Visual Studio, mais avec une interface utilisateur simplifiée.

- [Tutorial - Débogage d’une application .NET Core avec Visual Studio Code](../tutorials/with-visual-studio-code.md#debug)
- [Débogage dans Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)
