---
ms.openlocfilehash: 959d8cb6d3e52916f6777054f3e9b327dc8edb4e
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434928"
---
### <a name="global-assembly-cache-apis-are-obsolete"></a><span data-ttu-id="e84ae-101">Les API du global assembly cache sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="e84ae-101">Global assembly cache APIs are obsolete</span></span>

<span data-ttu-id="e84ae-102">.NET Core et .NET 5,0 et versions ultérieures éliminent le concept de Global Assembly Cache (GAC) qui était présent dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e84ae-102">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="e84ae-103">Ainsi, toutes les API .NET Core et .NET 5 + qui gèrent le GAC échouent ou n’effectuent aucune opération.</span><span class="sxs-lookup"><span data-stu-id="e84ae-103">As such, all .NET Core and .NET 5+ APIs that deal with the GAC either fail or perform no operation.</span></span>

<span data-ttu-id="e84ae-104">Pour aider les développeurs à s’éloigner de ces API, certaines API liées au GAC sont marquées comme obsolètes et génèrent un `SYSLIB0005` avertissement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e84ae-104">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, and generate a `SYSLIB0005` warning at compile time.</span></span> <span data-ttu-id="e84ae-105">Ces API peuvent être supprimées dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="e84ae-105">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e84ae-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e84ae-106">Change description</span></span>

<span data-ttu-id="e84ae-107">Les API suivantes sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="e84ae-107">The following APIs are marked obsolete.</span></span>

| <span data-ttu-id="e84ae-108">API</span><span class="sxs-lookup"><span data-stu-id="e84ae-108">API</span></span> | <span data-ttu-id="e84ae-109">Marqué comme obsolète dans...</span><span class="sxs-lookup"><span data-stu-id="e84ae-109">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | <span data-ttu-id="e84ae-110">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="e84ae-110">5.0 RC1</span></span> |

<span data-ttu-id="e84ae-111">Dans .NET Framework 2. x-4. x, la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété retourne `true` si l’assembly interrogé a été chargé à partir du GAC et `false` s’il a été chargé à partir d’un emplacement différent sur le disque.</span><span class="sxs-lookup"><span data-stu-id="e84ae-111">In .NET Framework 2.x - 4.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property returns `true` if the queried assembly was loaded from the GAC, and `false` if it was loaded from a different location on disk.</span></span> <span data-ttu-id="e84ae-112">Dans .NET Core 2. x-3. x, <xref:System.Reflection.Assembly.GlobalAssemblyCache> retourne toujours `false` , ce qui reflète le fait que le GAC n’existe pas dans .net core.</span><span class="sxs-lookup"><span data-stu-id="e84ae-112">In .NET Core 2.x - 3.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> always returns `false`, reflecting that the GAC does not exist in .NET Core.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="e84ae-113">Dans .NET 5,0 et versions ultérieures, la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété continue de retourner toujours `false` .</span><span class="sxs-lookup"><span data-stu-id="e84ae-113">In .NET 5.0 and later versions, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property continues to always return `false`.</span></span> <span data-ttu-id="e84ae-114">Toutefois, l’accesseur Get de propriété est également marqué comme obsolète pour indiquer aux appelants qu’ils doivent arrêter d’accéder à la propriété.</span><span class="sxs-lookup"><span data-stu-id="e84ae-114">However, the property getter is also marked as obsolete to indicate to callers that they should stop accessing the property.</span></span> <span data-ttu-id="e84ae-115">Les bibliothèques et les applications ne doivent pas utiliser l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> API pour effectuer des déterminations sur le comportement au moment de l’exécution, car elles sont toujours renvoyées `false` dans .net Core et .net 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e84ae-115">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5.0 and later versions.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="e84ae-116">Il s’agit d’une modification uniquement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e84ae-116">This is a compile-time only change.</span></span> <span data-ttu-id="e84ae-117">Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e84ae-117">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e84ae-118">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="e84ae-118">Reason for change</span></span>

<span data-ttu-id="e84ae-119">Le Global Assembly Cache (GAC) n’existe pas en tant que concept dans .NET Core et .NET 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e84ae-119">The global assembly cache (GAC) does not exist as a concept in .NET Core and .NET 5.0 and later versions.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e84ae-120">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e84ae-120">Version introduced</span></span>

<span data-ttu-id="e84ae-121">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e84ae-121">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e84ae-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e84ae-122">Recommended action</span></span>

- <span data-ttu-id="e84ae-123">Si votre application interroge la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété, envisagez de supprimer l’appel.</span><span class="sxs-lookup"><span data-stu-id="e84ae-123">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="e84ae-124">Si vous utilisez la <xref:System.Reflection.Assembly.GlobalAssemblyCache> valeur pour choisir entre un « assembly dans le GAC » et un « assembly qui n’est pas dans le GAC » au moment de l’exécution, reconsidérez si le workflow a toujours un sens pour une application .net Core ou .net 5.0 +.</span><span class="sxs-lookup"><span data-stu-id="e84ae-124">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET Core or .NET 5.0+ application.</span></span>

- <span data-ttu-id="e84ae-125">Si vous devez continuer à utiliser les API obsolètes, vous pouvez supprimer l' `SYSLIB0005` avertissement dans le code.</span><span class="sxs-lookup"><span data-stu-id="e84ae-125">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0005` warning in code.</span></span>

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  <span data-ttu-id="e84ae-126">Vous pouvez également supprimer l’avertissement dans votre fichier projet, ce qui désactive l’avertissement pour tous les fichiers sources du projet.</span><span class="sxs-lookup"><span data-stu-id="e84ae-126">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="e84ae-127">La suppression `SYSLIB0005` désactive uniquement l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> Avertissement obsoletion.</span><span class="sxs-lookup"><span data-stu-id="e84ae-127">Suppressing `SYSLIB0005` disables only the <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion warning.</span></span> <span data-ttu-id="e84ae-128">Il ne désactive pas les autres avertissements.</span><span class="sxs-lookup"><span data-stu-id="e84ae-128">It does not disable any other warnings.</span></span>

#### <a name="category"></a><span data-ttu-id="e84ae-129">Category</span><span class="sxs-lookup"><span data-stu-id="e84ae-129">Category</span></span>

<span data-ttu-id="e84ae-130">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="e84ae-130">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e84ae-131">API affectées</span><span class="sxs-lookup"><span data-stu-id="e84ae-131">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
