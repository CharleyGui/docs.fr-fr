---
title: 'Modification avec rupture : les API de communication à distance sont obsolètes'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où certaines API liées à la communication à distance sont marquées comme obsolètes et génèrent un avertissement avec un ID de diagnostic personnalisé.
ms.date: 11/01/2020
ms.openlocfilehash: 5687b1471028b077674cfd31cb77ce95dc51bef5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760987"
---
# <a name="remoting-apis-are-obsolete"></a><span data-ttu-id="d3a0f-103">Les API de communication à distance sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="d3a0f-103">Remoting APIs are obsolete</span></span>

<span data-ttu-id="d3a0f-104">Certaines API liées à la communication à distance sont marquées comme obsolètes et génèrent un `SYSLIB0010` avertissement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-104">Some remoting-related APIs are marked as obsolete and generate a `SYSLIB0010` warning at compile time.</span></span> <span data-ttu-id="d3a0f-105">Ces API peuvent être supprimées dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-105">These APIs may be removed in a future version of .NET.</span></span>

## <a name="change-description"></a><span data-ttu-id="d3a0f-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d3a0f-106">Change description</span></span>

<span data-ttu-id="d3a0f-107">Les API de communication à distance suivantes sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-107">The following remoting APIs are marked obsolete.</span></span>

| <span data-ttu-id="d3a0f-108">API</span><span class="sxs-lookup"><span data-stu-id="d3a0f-108">API</span></span> | <span data-ttu-id="d3a0f-109">Marqué comme obsolète dans...</span><span class="sxs-lookup"><span data-stu-id="d3a0f-109">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="d3a0f-110">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="d3a0f-110">5.0 RC1</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="d3a0f-111">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="d3a0f-111">5.0 RC1</span></span> |

<span data-ttu-id="d3a0f-112">Dans .NET Framework 2. x-4. x, les <xref:System.MarshalByRefObject.GetLifetimeService> <xref:System.MarshalByRefObject.InitializeLifetimeService> méthodes et contrôlent la durée de vie des instances impliquées dans .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-112">In .NET Framework 2.x - 4.x, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods control the lifetime of instances involved with .NET remoting.</span></span> <span data-ttu-id="d3a0f-113">Dans .NET Core 2. x-3. x, ces méthodes lèvent toujours une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-113">In .NET Core 2.x- 3.x, these methods always throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="d3a0f-114">Dans .NET 5,0 et versions ultérieures, <xref:System.MarshalByRefObject.GetLifetimeService> les <xref:System.MarshalByRefObject.InitializeLifetimeService> méthodes et sont marquées comme obsolètes comme avertissements, mais continuent à lever une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-114">In .NET 5.0 and later versions, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods are marked obsolete as warning, but continue to throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

<span data-ttu-id="d3a0f-115">Il s’agit d’une modification uniquement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-115">This is a compile-time only change.</span></span> <span data-ttu-id="d3a0f-116">Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-116">There is no run-time change from previous versions of .NET Core.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d3a0f-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d3a0f-117">Reason for change</span></span>

<span data-ttu-id="d3a0f-118">[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) est une technologie héritée.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-118">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology.</span></span> <span data-ttu-id="d3a0f-119">Il permet l’instanciation d’un objet dans un autre processus (peut-être même sur un autre ordinateur) et l’interaction avec cet objet comme s’il s’agissait d’une instance d’objet .NET en cours de traitement ordinaire.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-119">It allows instantiating an object in another process (potentially even on a different machine) and interacting with that object as if it were an ordinary, in-process .NET object instance.</span></span> <span data-ttu-id="d3a0f-120">L’infrastructure .NET Remoting existe uniquement dans .NET Framework 2. x-4. x.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-120">The .NET remoting infrastructure only exists in .NET Framework 2.x - 4.x.</span></span> <span data-ttu-id="d3a0f-121">.NET Core et .NET 5,0 et versions ultérieures ne prennent pas en charge .NET Remoting, et les API de communication à distance n’existent pas ou lèvent toujours des exceptions sur ces runtimes.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-121">.NET Core and .NET 5.0 and later versions don't have support for .NET remoting, and the remoting APIs either don't exist or always throw exceptions on these runtimes.</span></span>

<span data-ttu-id="d3a0f-122">Pour aider les développeurs à s’éloigner de ces API, nous avons Obsoleting les API liées à la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-122">To help steer developers away from these APIs, we are obsoleting selected remoting-related APIs.</span></span> <span data-ttu-id="d3a0f-123">Ces API peuvent être supprimées entièrement dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-123">These APIs may be removed entirely in a future version of .NET.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d3a0f-124">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d3a0f-124">Version introduced</span></span>

<span data-ttu-id="d3a0f-125">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d3a0f-125">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d3a0f-126">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d3a0f-126">Recommended action</span></span>

- <span data-ttu-id="d3a0f-127">Envisagez d’utiliser des services REST WCF ou HTTP pour communiquer avec des objets dans d’autres applications ou sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-127">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="d3a0f-128">Pour plus d’informations, consultez [.NET Framework technologies indisponibles sur .net Core](../../../porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="d3a0f-128">For more information, see [.NET Framework technologies unavailable on .NET Core](../../../porting/net-framework-tech-unavailable.md).</span></span>

- <span data-ttu-id="d3a0f-129">Si vous devez continuer à utiliser les API obsolètes, vous pouvez supprimer l' `SYSLIB0010` avertissement dans le code.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-129">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0010` warning in code.</span></span>

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  <span data-ttu-id="d3a0f-130">Vous pouvez également supprimer l’avertissement dans votre fichier projet, ce qui désactive l’avertissement pour tous les fichiers sources du projet.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-130">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="d3a0f-131">La suppression `SYSLIB0010` désactive uniquement les avertissements obsoletion de l’API de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-131">Suppressing `SYSLIB0010` disables only the remoting API obsoletion warnings.</span></span> <span data-ttu-id="d3a0f-132">Il ne désactive pas les autres avertissements.</span><span class="sxs-lookup"><span data-stu-id="d3a0f-132">It does not disable any other warnings.</span></span> <span data-ttu-id="d3a0f-133">En outre, il ne modifie pas le comportement de l’exécution codé en continu de Always levant <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="d3a0f-133">Additionally, it doesn't change the hardcoded run-time behavior of always throwing <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d3a0f-134">API affectées</span><span class="sxs-lookup"><span data-stu-id="d3a0f-134">Affected APIs</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
