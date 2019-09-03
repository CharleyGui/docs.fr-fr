---
title: Débogueurs managés-.NET Core
description: Vue d’ensemble de Visual Studio et Visual Studio Code les débogueurs managés.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 8110ecb10ad2e6213e15df8848abab73d07d89b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "70234646"
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
