---
ms.openlocfilehash: 35041a035041fd4ad5402e1bc0dd137a74d4f949
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434924"
---
### <a name="remoting-apis-are-obsolete"></a><span data-ttu-id="09b02-101">Les API de communication à distance sont obsolètes</span><span class="sxs-lookup"><span data-stu-id="09b02-101">Remoting APIs are obsolete</span></span>

<span data-ttu-id="09b02-102">Certaines API liées à la communication à distance sont marquées comme obsolètes et génèrent un `SYSLIB0010` avertissement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="09b02-102">Some remoting-related APIs are marked as obsolete and generate a `SYSLIB0010` warning at compile time.</span></span> <span data-ttu-id="09b02-103">Ces API peuvent être supprimées dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="09b02-103">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="09b02-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="09b02-104">Change description</span></span>

<span data-ttu-id="09b02-105">Les API de communication à distance suivantes sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="09b02-105">The following remoting APIs are marked obsolete.</span></span>

| <span data-ttu-id="09b02-106">API</span><span class="sxs-lookup"><span data-stu-id="09b02-106">API</span></span> | <span data-ttu-id="09b02-107">Marqué comme obsolète dans...</span><span class="sxs-lookup"><span data-stu-id="09b02-107">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="09b02-108">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="09b02-108">5.0 RC1</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="09b02-109">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="09b02-109">5.0 RC1</span></span> |

<span data-ttu-id="09b02-110">Dans .NET Framework 2. x-4. x, les <xref:System.MarshalByRefObject.GetLifetimeService> <xref:System.MarshalByRefObject.InitializeLifetimeService> méthodes et contrôlent la durée de vie des instances impliquées dans .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="09b02-110">In .NET Framework 2.x - 4.x, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods control the lifetime of instances involved with .NET remoting.</span></span> <span data-ttu-id="09b02-111">Dans .NET Core 2. x-3. x, ces méthodes lèvent toujours une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="09b02-111">In .NET Core 2.x- 3.x, these methods always throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="09b02-112">Dans .NET 5,0 et versions ultérieures, <xref:System.MarshalByRefObject.GetLifetimeService> les <xref:System.MarshalByRefObject.InitializeLifetimeService> méthodes et sont marquées comme obsolètes comme avertissements, mais continuent à lever une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="09b02-112">In .NET 5.0 and later versions, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods are marked obsolete as warning, but continue to throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

<span data-ttu-id="09b02-113">Il s’agit d’une modification uniquement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="09b02-113">This is a compile-time only change.</span></span> <span data-ttu-id="09b02-114">Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="09b02-114">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="09b02-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="09b02-115">Reason for change</span></span>

<span data-ttu-id="09b02-116">[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) est une technologie héritée.</span><span class="sxs-lookup"><span data-stu-id="09b02-116">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology.</span></span> <span data-ttu-id="09b02-117">Il permet l’instanciation d’un objet dans un autre processus (peut-être même sur un autre ordinateur) et l’interaction avec cet objet comme s’il s’agissait d’une instance d’objet .NET en cours de traitement ordinaire.</span><span class="sxs-lookup"><span data-stu-id="09b02-117">It allows instantiating an object in another process (potentially even on a different machine) and interacting with that object as if it were an ordinary, in-process .NET object instance.</span></span> <span data-ttu-id="09b02-118">L’infrastructure .NET Remoting existe uniquement dans .NET Framework 2. x-4. x.</span><span class="sxs-lookup"><span data-stu-id="09b02-118">The .NET remoting infrastructure only exists in .NET Framework 2.x - 4.x.</span></span> <span data-ttu-id="09b02-119">.NET Core et .NET 5,0 et versions ultérieures ne prennent pas en charge .NET Remoting, et les API de communication à distance n’existent pas ou lèvent toujours des exceptions sur ces runtimes.</span><span class="sxs-lookup"><span data-stu-id="09b02-119">.NET Core and .NET 5.0 and later versions don't have support for .NET remoting, and the remoting APIs either don't exist or always throw exceptions on these runtimes.</span></span>

<span data-ttu-id="09b02-120">Pour aider les développeurs à s’éloigner de ces API, nous avons Obsoleting les API liées à la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="09b02-120">To help steer developers away from these APIs, we are obsoleting selected remoting-related APIs.</span></span> <span data-ttu-id="09b02-121">Ces API peuvent être supprimées entièrement dans une future version de .NET.</span><span class="sxs-lookup"><span data-stu-id="09b02-121">These APIs may be removed entirely in a future version of .NET.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="09b02-122">Version introduite</span><span class="sxs-lookup"><span data-stu-id="09b02-122">Version introduced</span></span>

<span data-ttu-id="09b02-123">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="09b02-123">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="09b02-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="09b02-124">Recommended action</span></span>

- <span data-ttu-id="09b02-125">Envisagez d’utiliser des services REST WCF ou HTTP pour communiquer avec des objets dans d’autres applications ou sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="09b02-125">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="09b02-126">Pour plus d’informations, consultez [.NET Framework technologies indisponibles sur .net Core](../../../../docs/core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="09b02-126">For more information, see [.NET Framework technologies unavailable on .NET Core](../../../../docs/core/porting/net-framework-tech-unavailable.md).</span></span>

- <span data-ttu-id="09b02-127">Si vous devez continuer à utiliser les API obsolètes, vous pouvez supprimer l' `SYSLIB0010` avertissement dans le code.</span><span class="sxs-lookup"><span data-stu-id="09b02-127">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0010` warning in code.</span></span>

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  <span data-ttu-id="09b02-128">Vous pouvez également supprimer l’avertissement dans votre fichier projet, ce qui désactive l’avertissement pour tous les fichiers sources du projet.</span><span class="sxs-lookup"><span data-stu-id="09b02-128">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="09b02-129">La suppression `SYSLIB0010` désactive uniquement les avertissements obsoletion de l’API de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="09b02-129">Suppressing `SYSLIB0010` disables only the remoting API obsoletion warnings.</span></span> <span data-ttu-id="09b02-130">Il ne désactive pas les autres avertissements.</span><span class="sxs-lookup"><span data-stu-id="09b02-130">It does not disable any other warnings.</span></span> <span data-ttu-id="09b02-131">En outre, il ne modifie pas le comportement de l’exécution codé en continu de Always levant <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="09b02-131">Additionally, it doesn't change the hardcoded run-time behavior of always throwing <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="09b02-132">Category</span><span class="sxs-lookup"><span data-stu-id="09b02-132">Category</span></span>

<span data-ttu-id="09b02-133">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="09b02-133">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="09b02-134">API affectées</span><span class="sxs-lookup"><span data-stu-id="09b02-134">Affected APIs</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
