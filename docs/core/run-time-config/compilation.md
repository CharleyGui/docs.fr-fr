---
title: Paramètres de configuration de compilation
description: En savoir plus sur les paramètres d’exécution qui configurent le fonctionnement du compilateur JIT pour les applications .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802819"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="11181-103">Options de configuration au moment de l’exécution pour la compilation</span><span class="sxs-lookup"><span data-stu-id="11181-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="11181-104">Compilation hiérarchisée</span><span class="sxs-lookup"><span data-stu-id="11181-104">Tiered compilation</span></span>

- <span data-ttu-id="11181-105">Configure si le compilateur JIT utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="11181-105">Configures whether the JIT compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>
- <span data-ttu-id="11181-106">Dans .NET Core 3,0 et versions ultérieures, la compilation à plusieurs niveaux est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="11181-106">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="11181-107">Dans .NET Core 2,1 et 2,2, la compilation à plusieurs niveaux est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="11181-107">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>

| | <span data-ttu-id="11181-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="11181-108">Setting name</span></span> | <span data-ttu-id="11181-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="11181-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="11181-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="11181-110">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="11181-111">activé `true`</span><span class="sxs-lookup"><span data-stu-id="11181-111">`true` - enabled</span></span><br/><span data-ttu-id="11181-112">`false`-désactivé</span><span class="sxs-lookup"><span data-stu-id="11181-112">`false` - disabled</span></span> |
| <span data-ttu-id="11181-113">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="11181-113">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="11181-114">activé `1`</span><span class="sxs-lookup"><span data-stu-id="11181-114">`1` - enabled</span></span><br/><span data-ttu-id="11181-115">`0`-désactivé</span><span class="sxs-lookup"><span data-stu-id="11181-115">`0` - disabled</span></span> |
