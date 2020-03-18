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
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="257f5-103">.NET Core a géré les débbuggeurs</span><span class="sxs-lookup"><span data-stu-id="257f5-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="257f5-104">Les débbuggeurs permettent aux programmes d’être mis en pause ou exécutés étape par étape.</span><span class="sxs-lookup"><span data-stu-id="257f5-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="257f5-105">Une fois mis en pause, l’état actuel du processus peut être consulté.</span><span class="sxs-lookup"><span data-stu-id="257f5-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="257f5-106">En franchiant les sections clés, vous obtenez une compréhension de votre code et pourquoi il produit le résultat qu’il fait.</span><span class="sxs-lookup"><span data-stu-id="257f5-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="257f5-107">Microsoft fournit des débbuggers pour le code géré dans **Visual Studio** et Visual **Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="257f5-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="257f5-108">Visual Studio géré débbugger</span><span class="sxs-lookup"><span data-stu-id="257f5-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="257f5-109">**Visual Studio** est un environnement de développement intégré avec le débbuggeur le plus complet disponible.</span><span class="sxs-lookup"><span data-stu-id="257f5-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="257f5-110">Visual Studio est un excellent choix pour les développeurs travaillant sur Windows.</span><span class="sxs-lookup"><span data-stu-id="257f5-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="257f5-111">Tutorial - Débogage d’une application .NET Core sur Windows avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="257f5-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="257f5-112">Bien que Visual Studio soit une application Windows, il peut toujours être utilisé pour déboiffer les applications Linux et macOS à distance.</span><span class="sxs-lookup"><span data-stu-id="257f5-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="257f5-113">Déboguer une application .NET Core sur Linux/OSX avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="257f5-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="257f5-114">Le débogage ASP.NET les applications Core nécessitent des instructions légèrement différentes.</span><span class="sxs-lookup"><span data-stu-id="257f5-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="257f5-115">Debug ASP.NET applications De Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="257f5-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="257f5-116">Code de studio visuel géré débrisonneur</span><span class="sxs-lookup"><span data-stu-id="257f5-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="257f5-117">**Visual Studio Code** est un éditeur de code multiplateforme léger.</span><span class="sxs-lookup"><span data-stu-id="257f5-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="257f5-118">Il utilise la même implémentation .NET Core debugger que Visual Studio, mais avec une interface utilisateur simplifiée.</span><span class="sxs-lookup"><span data-stu-id="257f5-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="257f5-119">Tutorial - Débogage d’une application .NET Core avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="257f5-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="257f5-120">Débogage dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="257f5-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
