---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974147"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="cfa0f-103">Quels sont les outils de diagnostic disponibles dans .NET Core ?</span><span class="sxs-lookup"><span data-stu-id="cfa0f-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="cfa0f-104">Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="cfa0f-105">Cet article vous aide à trouver les différents outils dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggersmanaged-debuggersmd"></a>[<span data-ttu-id="cfa0f-106">Débogueurs gérés</span><span class="sxs-lookup"><span data-stu-id="cfa0f-106">Managed debuggers</span></span>](managed-debuggers.md)
<span data-ttu-id="cfa0f-107">Les débogueurs gérés vous permettent d'interagir avec votre programme.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-107">Managed debuggers allow you to interact with your program.</span></span> <span data-ttu-id="cfa0f-108">La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="cfa0f-109">Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracinglogging-tracingmd"></a>[<span data-ttu-id="cfa0f-110">Journalisation et suivi</span><span class="sxs-lookup"><span data-stu-id="cfa0f-110">Logging and tracing</span></span>](logging-tracing.md)
<span data-ttu-id="cfa0f-111">La journalisation et le suivi sont des techniques connexes.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-111">Logging and tracing are related techniques.</span></span> <span data-ttu-id="cfa0f-112">Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="cfa0f-113">Les fichiers consignent le détail des tâches exécutées par un programme.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-113">The files record the details of what a program does.</span></span> <span data-ttu-id="cfa0f-114">Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="cfa0f-115">Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testingtestingindexmd"></a>[<span data-ttu-id="cfa0f-116">Tests unitaires</span><span class="sxs-lookup"><span data-stu-id="cfa0f-116">Unit testing</span></span>](../testing/index.md)
<span data-ttu-id="cfa0f-117">Le test unitaire est un élément clé de l'intégration et du déploiement continus de logiciels de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-117">Unit testing is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="cfa0f-118">Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.</span><span class="sxs-lookup"><span data-stu-id="cfa0f-118">Unit tests are designed to give you an early warning when you break something.</span></span>
