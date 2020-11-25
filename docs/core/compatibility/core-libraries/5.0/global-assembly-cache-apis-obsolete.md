---
title: 'Modification avec rupture : les API du global assembly cache sont obsolètes'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où les API qui traitent le GAC échouent ou n’effectuent aucune opération.
ms.date: 11/01/2020
ms.openlocfilehash: 2f74fccc68b7a925d909938d77578df8ebe8d60d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761064"
---
# <a name="global-assembly-cache-apis-are-obsolete"></a><span data-ttu-id="3eb22-103">Les API du global assembly cache sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="3eb22-103">Global assembly cache APIs are obsolete</span></span>

<span data-ttu-id="3eb22-104">.NET Core et .NET 5,0 et versions ultérieures éliminent le concept de Global Assembly Cache (GAC) qui était présent dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3eb22-104">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="3eb22-105">Ainsi, toutes les API .NET Core et .NET 5 + qui gèrent le GAC échouent ou n’effectuent aucune opération.</span><span class="sxs-lookup"><span data-stu-id="3eb22-105">As such, all .NET Core and .NET 5+ APIs that deal with the GAC either fail or perform no operation.</span></span>

<span data-ttu-id="3eb22-106">Pour aider les développeurs à s’éloigner de ces API, certaines API liées au GAC sont marquées comme obsolètes et génèrent un `SYSLIB0005` avertissement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="3eb22-106">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, and generate a `SYSLIB0005` warning at compile time.</span></span> <span data-ttu-id="3eb22-107">Ces API peuvent être supprimées dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="3eb22-107">These APIs may be removed in a future version of .NET.</span></span>

## <a name="change-description"></a><span data-ttu-id="3eb22-108">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3eb22-108">Change description</span></span>

<span data-ttu-id="3eb22-109">Les API suivantes sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="3eb22-109">The following APIs are marked obsolete.</span></span>

| <span data-ttu-id="3eb22-110">API</span><span class="sxs-lookup"><span data-stu-id="3eb22-110">API</span></span> | <span data-ttu-id="3eb22-111">Marqué comme obsolète dans...</span><span class="sxs-lookup"><span data-stu-id="3eb22-111">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | <span data-ttu-id="3eb22-112">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="3eb22-112">5.0 RC1</span></span> |

<span data-ttu-id="3eb22-113">Dans .NET Framework 2. x-4. x, la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété retourne `true` si l’assembly interrogé a été chargé à partir du GAC et `false` s’il a été chargé à partir d’un emplacement différent sur le disque.</span><span class="sxs-lookup"><span data-stu-id="3eb22-113">In .NET Framework 2.x - 4.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property returns `true` if the queried assembly was loaded from the GAC, and `false` if it was loaded from a different location on disk.</span></span> <span data-ttu-id="3eb22-114">Dans .NET Core 2. x-3. x, <xref:System.Reflection.Assembly.GlobalAssemblyCache> retourne toujours `false` , ce qui reflète le fait que le GAC n’existe pas dans .net core.</span><span class="sxs-lookup"><span data-stu-id="3eb22-114">In .NET Core 2.x - 3.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> always returns `false`, reflecting that the GAC does not exist in .NET Core.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="3eb22-115">Dans .NET 5,0 et versions ultérieures, la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété continue de retourner toujours `false` .</span><span class="sxs-lookup"><span data-stu-id="3eb22-115">In .NET 5.0 and later versions, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property continues to always return `false`.</span></span> <span data-ttu-id="3eb22-116">Toutefois, l’accesseur Get de propriété est également marqué comme obsolète pour indiquer aux appelants qu’ils doivent arrêter d’accéder à la propriété.</span><span class="sxs-lookup"><span data-stu-id="3eb22-116">However, the property getter is also marked as obsolete to indicate to callers that they should stop accessing the property.</span></span> <span data-ttu-id="3eb22-117">Les bibliothèques et les applications ne doivent pas utiliser l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> API pour effectuer des déterminations sur le comportement au moment de l’exécution, car elles sont toujours renvoyées `false` dans .net Core et .net 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3eb22-117">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5.0 and later versions.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="3eb22-118">Il s’agit d’une modification uniquement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="3eb22-118">This is a compile-time only change.</span></span> <span data-ttu-id="3eb22-119">Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3eb22-119">There is no run-time change from previous versions of .NET Core.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3eb22-120">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="3eb22-120">Reason for change</span></span>

<span data-ttu-id="3eb22-121">Le Global Assembly Cache (GAC) n’existe pas en tant que concept dans .NET Core et .NET 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3eb22-121">The global assembly cache (GAC) does not exist as a concept in .NET Core and .NET 5.0 and later versions.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3eb22-122">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3eb22-122">Version introduced</span></span>

<span data-ttu-id="3eb22-123">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3eb22-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3eb22-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3eb22-124">Recommended action</span></span>

- <span data-ttu-id="3eb22-125">Si votre application interroge la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété, envisagez de supprimer l’appel.</span><span class="sxs-lookup"><span data-stu-id="3eb22-125">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="3eb22-126">Si vous utilisez la <xref:System.Reflection.Assembly.GlobalAssemblyCache> valeur pour choisir entre un « assembly dans le GAC » et un « assembly qui n’est pas dans le GAC » au moment de l’exécution, reconsidérez si le workflow a toujours un sens pour une application .net Core ou .net 5.0 +.</span><span class="sxs-lookup"><span data-stu-id="3eb22-126">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET Core or .NET 5.0+ application.</span></span>

- <span data-ttu-id="3eb22-127">Si vous devez continuer à utiliser les API obsolètes, vous pouvez supprimer l' `SYSLIB0005` avertissement dans le code.</span><span class="sxs-lookup"><span data-stu-id="3eb22-127">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0005` warning in code.</span></span>

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  <span data-ttu-id="3eb22-128">Vous pouvez également supprimer l’avertissement dans votre fichier projet, ce qui désactive l’avertissement pour tous les fichiers sources du projet.</span><span class="sxs-lookup"><span data-stu-id="3eb22-128">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="3eb22-129">La suppression `SYSLIB0005` désactive uniquement l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> Avertissement obsoletion.</span><span class="sxs-lookup"><span data-stu-id="3eb22-129">Suppressing `SYSLIB0005` disables only the <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion warning.</span></span> <span data-ttu-id="3eb22-130">Il ne désactive pas les autres avertissements.</span><span class="sxs-lookup"><span data-stu-id="3eb22-130">It does not disable any other warnings.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3eb22-131">API affectées</span><span class="sxs-lookup"><span data-stu-id="3eb22-131">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
