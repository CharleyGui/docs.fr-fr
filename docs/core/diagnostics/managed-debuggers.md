---
title: Débogueurs managés-.NET Core
description: Vue d’ensemble de Visual Studio et Visual Studio Code les débogueurs managés.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 3741011d22ab6c4240b7f88a9ab790ea61ecd0d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926438"
---
# <a name="net-core-managed-debuggers"></a>Débogueurs managés .NET Core

Les débogueurs permettent de suspendre ou d’exécuter les programmes pas à pas. Lorsqu’elle est suspendue, l’état actuel du processus peut être affiché. En exécutant pas à pas les sections clés, vous vous familiarisez avec votre code et pourquoi il produit le résultat qu’il fait.

Microsoft fournit des débogueurs pour le code managé dans **Visual Studio** et **Visual Studio code**.

## <a name="visual-studio-managed-debugger"></a>Débogueur managé Visual Studio

**Visual Studio** est un environnement de développement intégré avec le débogueur le plus complet disponible. Visual Studio est un excellent choix pour les développeurs qui travaillent sur Windows.

- [Didacticiel-débogage d’une application .NET Core sur Windows avec Visual Studio](../tutorials/debugging-with-visual-studio.md)

Alors que Visual Studio est une application Windows, il peut toujours être utilisé pour déboguer des applications Linux et macOS à distance.

- [Débogage d’une application .NET Core sur Linux/OSX avec Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 Le débogage des applications ASP.NET Core nécessite des instructions légèrement différentes.

- [Déboguer des applications ASP.NET Core dans Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Débogueur géré par Visual Studio Code

**Visual Studio code** est un éditeur de code multiplateforme léger. Il utilise la même implémentation du débogueur .NET Core que Visual Studio, mais avec une interface utilisateur simplifiée.

- [Didacticiel-débogage d’une application .NET Core avec Visual Studio Code](../tutorials/with-visual-studio-code.md#debug)
- [Débogage dans Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)
