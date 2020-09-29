---
ms.openlocfilehash: 8693c1fdef5fa194b16127d4f1dd87e23ad68f2d
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438042"
---
### <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a><span data-ttu-id="3bc73-101">La conversion du wrapper RCW en `InterfaceIsIInspectable` interface lève PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="3bc73-101">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>

<span data-ttu-id="3bc73-102">Le cast d’un wrapper RCW (Runtime Callable Wrapper) en une interface marquée comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> lève désormais une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="3bc73-102">Casting a runtime callable wrapper (RCW) to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> now throws a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="3bc73-103">Ce changement est un suivi de la [Suppression de la prise en charge WinRT de .net](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span><span class="sxs-lookup"><span data-stu-id="3bc73-103">This change is a follow up to the [removal of WinRT support from .NET](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3bc73-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3bc73-104">Version introduced</span></span>

<span data-ttu-id="3bc73-105">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="3bc73-105">5.0 RC2</span></span>

#### <a name="change-description"></a><span data-ttu-id="3bc73-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3bc73-106">Change description</span></span>

<span data-ttu-id="3bc73-107">Dans les versions .NET antérieures à .NET 5,0 Preview 6, le fait de convertir un wrapper RCW en une interface marquée comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> fonctionnait comme prévu.</span><span class="sxs-lookup"><span data-stu-id="3bc73-107">In .NET versions prior to .NET 5.0 preview 6, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> works as expected.</span></span> <span data-ttu-id="3bc73-108">Dans .NET 5,0 préversions 6-8 et RC1, vous pouvez réussir le cast d’un wrapper RCW en <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span><span class="sxs-lookup"><span data-stu-id="3bc73-108">In .NET 5.0 previews 6-8 and RC1, you can successfully cast an RCW to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span></span> <span data-ttu-id="3bc73-109">Toutefois, vous pouvez obtenir des violations d’accès lorsque vous exécutez des méthodes sur l’interface, car la prise en charge sous-jacente dans le runtime [a été supprimée dans .net 5,0 Preview 6](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span><span class="sxs-lookup"><span data-stu-id="3bc73-109">However, you might get access violations when you execute methods on the interface, because the underlying support in the runtime [was removed in .NET 5.0 preview 6](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

<span data-ttu-id="3bc73-110">Dans .NET 5,0 RC2 et versions ultérieures, le cast d’un wrapper RCW en une interface marquée comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> lève une <xref:System.PlatformNotSupportedException> au moment de la conversion.</span><span class="sxs-lookup"><span data-stu-id="3bc73-110">In .NET 5.0 RC2 and later versions, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> throws a <xref:System.PlatformNotSupportedException> at cast time.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3bc73-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="3bc73-111">Reason for change</span></span>

<span data-ttu-id="3bc73-112">La prise en charge de <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> a été [supprimée dans une version précédente de .net 5,0 Preview](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span><span class="sxs-lookup"><span data-stu-id="3bc73-112">The support for <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> was [removed in a previous .NET 5.0 preview](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span> <span data-ttu-id="3bc73-113">Toutefois, une conversion vers une <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface a été accidentellement négligée.</span><span class="sxs-lookup"><span data-stu-id="3bc73-113">However, casting to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface was accidentally overlooked.</span></span> <span data-ttu-id="3bc73-114">Étant donné que la prise en charge sous-jacente dans le runtime n’existe plus, la levée d’un <xref:System.PlatformNotSupportedException> permet d’obtenir un chemin d’échec normal.</span><span class="sxs-lookup"><span data-stu-id="3bc73-114">Since the underlying support in the runtime no longer exists, throwing a <xref:System.PlatformNotSupportedException> enables a graceful failure path.</span></span> <span data-ttu-id="3bc73-115">La levée d’une exception rend également plus détectable que cette fonctionnalité n’est plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3bc73-115">Throwing an exception also makes it more discoverable that this feature is no longer supported.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3bc73-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3bc73-116">Recommended action</span></span>

- <span data-ttu-id="3bc73-117">Si vous pouvez définir l’interface dans un fichier de métadonnées Windows Runtime (WinMD), utilisez l’outil C#/WinRT à la place.</span><span class="sxs-lookup"><span data-stu-id="3bc73-117">If you can define the interface in a Windows runtime metadata (WinMD) file, use the C#/WinRT tool instead.</span></span>

- <span data-ttu-id="3bc73-118">Sinon, marquez l’interface comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> au lieu de <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> , puis ajoutez trois entrées factices au début de l’interface pour les <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> méthodes.</span><span class="sxs-lookup"><span data-stu-id="3bc73-118">Otherwise, mark the interface as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> instead of <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, and add three dummy entries to the start of the interface for the <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> methods.</span></span> <span data-ttu-id="3bc73-119">L’extrait de code suivant montre un exemple.</span><span class="sxs-lookup"><span data-stu-id="3bc73-119">The following code snippet shows an example.</span></span>

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

#### <a name="category"></a><span data-ttu-id="3bc73-120">Category</span><span class="sxs-lookup"><span data-stu-id="3bc73-120">Category</span></span>

<span data-ttu-id="3bc73-121">Interop</span><span class="sxs-lookup"><span data-stu-id="3bc73-121">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3bc73-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="3bc73-122">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

-->
