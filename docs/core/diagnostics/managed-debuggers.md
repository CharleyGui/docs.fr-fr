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
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="8fd6f-103">Débogueurs managés .NET Core</span><span class="sxs-lookup"><span data-stu-id="8fd6f-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="8fd6f-104">Les débogueurs permettent de suspendre ou d’exécuter les programmes pas à pas.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="8fd6f-105">Lorsqu’elle est suspendue, l’état actuel du processus peut être affiché.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="8fd6f-106">En exécutant pas à pas les sections clés, vous vous familiarisez avec votre code et pourquoi il produit le résultat qu’il fait.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="8fd6f-107">Microsoft fournit des débogueurs pour le code managé dans **Visual Studio** et **Visual Studio code**.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="8fd6f-108">Débogueur managé Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fd6f-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="8fd6f-109">**Visual Studio** est un environnement de développement intégré avec le débogueur le plus complet disponible.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="8fd6f-110">Visual Studio est un excellent choix pour les développeurs qui travaillent sur Windows.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>
- [<span data-ttu-id="8fd6f-111">Didacticiel-débogage d’une application .NET Core sur Windows avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fd6f-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="8fd6f-112">Alors que Visual Studio est une application Windows, il peut toujours être utilisé pour déboguer des applications Linux et macOS à distance.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>
- [<span data-ttu-id="8fd6f-113">Débogage d’une application .NET Core sur Linux/OSX avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fd6f-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="8fd6f-114">Le débogage des applications ASP.NET Core nécessite des instructions légèrement différentes.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="8fd6f-115">Déboguer des applications ASP.NET Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fd6f-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="8fd6f-116">Débogueur géré par Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8fd6f-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="8fd6f-117">**Visual Studio code** est un éditeur de code multiplateforme léger.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="8fd6f-118">Il utilise la même implémentation du débogueur .NET Core que Visual Studio, mais avec une interface utilisateur simplifiée.</span><span class="sxs-lookup"><span data-stu-id="8fd6f-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="8fd6f-119">Didacticiel-débogage d’une application .NET Core avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8fd6f-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="8fd6f-120">Débogage dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8fd6f-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
