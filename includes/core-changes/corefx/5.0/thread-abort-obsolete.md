---
ms.openlocfilehash: ee67b32b093ebd42f8ac685b34b12f2f6833be86
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332919"
---
### <a name="threadabort-is-obsolete"></a><span data-ttu-id="e7a3c-101">Thread. Abort est obsolète</span><span class="sxs-lookup"><span data-stu-id="e7a3c-101">Thread.Abort is obsolete</span></span>

<span data-ttu-id="e7a3c-102">Les <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-102">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="e7a3c-103">Les projets qui ciblent .NET 5,0 ou une version ultérieure rencontreront un avertissement au moment de la compilation `SYSLIB0006` si ces méthodes sont appelées.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-103">Projects that target .NET 5.0 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e7a3c-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e7a3c-104">Change description</span></span>

<span data-ttu-id="e7a3c-105">Auparavant, les appels à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ne produisaient pas d’avertissements au moment de la compilation, mais la méthode avait levé une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-105">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="e7a3c-106">À compter de .NET 5,0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> est marqué comme obsolète en tant qu’avertissement.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-106">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="e7a3c-107">L’appel de cette méthode génère un avertissement du compilateur `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="e7a3c-107">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="e7a3c-108">L’implémentation de la méthode est inchangée et continue à lever une <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="e7a3c-108">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e7a3c-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="e7a3c-109">Reason for change</span></span>

<span data-ttu-id="e7a3c-110">Étant donné que <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> lève toujours une <xref:System.PlatformNotSupportedException> sur toutes les implémentations de .net, à l’exception de .NET Framework, <xref:System.ObsoleteAttribute> a été ajouté à la méthode pour attirer l’attention sur les endroits où elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-110">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7a3c-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e7a3c-111">Version introduced</span></span>

<span data-ttu-id="e7a3c-112">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="e7a3c-112">5.0 RC 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7a3c-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e7a3c-113">Recommended action</span></span>

- <span data-ttu-id="e7a3c-114">Utilisez un <xref:System.Threading.CancellationToken> pour abandonner le traitement d’une unité de travail au lieu d’appeler <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e7a3c-114">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e7a3c-115">L’exemple suivant illustre l’utilisation de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="e7a3c-115">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  <span data-ttu-id="e7a3c-116">Pour plus d’informations, consultez [Annulation dans les threads managés](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="e7a3c-116">For more information, see [Cancellation in managed threads](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="e7a3c-117">Pour supprimer l’avertissement au moment de la compilation, supprimez le code d’avertissement `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="e7a3c-117">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="e7a3c-118">Le code d’avertissement est spécifique à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> et sa suppression ne supprime pas les autres avertissements obsoletion dans votre code.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-118">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="e7a3c-119">Toutefois, nous vous recommandons de supprimer les appels au <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> au lieu de supprimer l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-119">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="e7a3c-120">Vous pouvez également supprimer l’avertissement dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="e7a3c-120">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="e7a3c-121">Category</span><span class="sxs-lookup"><span data-stu-id="e7a3c-121">Category</span></span>

- <span data-ttu-id="e7a3c-122">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="e7a3c-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7a3c-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="e7a3c-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
