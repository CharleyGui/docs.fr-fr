---
ms.openlocfilehash: 85488de561a2298f2ff4009ec78b9a6e294053f3
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598162"
---
### <a name="threadabort-is-obsolete"></a><span data-ttu-id="2ac96-101">Thread. Abort est obsolète</span><span class="sxs-lookup"><span data-stu-id="2ac96-101">Thread.Abort is obsolete</span></span>

<span data-ttu-id="2ac96-102">Les <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="2ac96-102">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="2ac96-103">Les projets qui ciblent .NET 5,0 ou une version ultérieure rencontreront des avertissements au moment de la compilation si ces méthodes sont appelées.</span><span class="sxs-lookup"><span data-stu-id="2ac96-103">Projects that target .NET 5.0 or a later version will encounter compile-time warnings if these methods are called.</span></span> <span data-ttu-id="2ac96-104">Si vous supprimez les avertissements, une <xref:System.PlatformNotSupportedException> est levée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2ac96-104">If you suppress the warnings, a <xref:System.PlatformNotSupportedException> will be thrown at run time.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2ac96-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="2ac96-105">Change description</span></span>

<span data-ttu-id="2ac96-106">Auparavant, les appels à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ne produisaient pas d’avertissements au moment de la compilation, mais la méthode avait levé une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2ac96-106">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="2ac96-107">À compter de .NET 5,0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> est marqué comme obsolète en tant qu’avertissement.</span><span class="sxs-lookup"><span data-stu-id="2ac96-107">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="2ac96-108">L’appel de cette méthode génère un avertissement du compilateur `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="2ac96-108">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="2ac96-109">L’implémentation de la méthode est inchangée et continue à lever une <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="2ac96-109">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2ac96-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2ac96-110">Reason for change</span></span>

<span data-ttu-id="2ac96-111">Étant donné que <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> lève toujours une <xref:System.PlatformNotSupportedException> sur toutes les implémentations de .net, à l’exception de .NET Framework, <xref:System.ObsoleteAttribute> a été ajouté à la méthode pour attirer l’attention sur les endroits où elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="2ac96-111">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ac96-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2ac96-112">Version introduced</span></span>

<span data-ttu-id="2ac96-113">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="2ac96-113">5.0 RC 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ac96-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2ac96-114">Recommended action</span></span>

- <span data-ttu-id="2ac96-115">Utilisez un <xref:System.Threading.CancellationToken> pour abandonner le traitement d’une unité de travail au lieu d’appeler <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2ac96-115">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2ac96-116">L’exemple suivant illustre l’utilisation de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="2ac96-116">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

  <span data-ttu-id="2ac96-117">Pour plus d’informations, consultez [Annulation dans les threads managés](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="2ac96-117">For more information, see [Cancellation in managed threads](../../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="2ac96-118">Pour supprimer l’avertissement au moment de la compilation, supprimez le code d’avertissement `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="2ac96-118">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="2ac96-119">Le code d’avertissement est spécifique à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> et sa suppression ne supprime pas les autres avertissements obsoletion dans votre code.</span><span class="sxs-lookup"><span data-stu-id="2ac96-119">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="2ac96-120">Toutefois, nous vous recommandons de supprimer les appels au <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> au lieu de supprimer l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="2ac96-120">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="2ac96-121">Vous pouvez également supprimer l’avertissement dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="2ac96-121">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="2ac96-122">Category</span><span class="sxs-lookup"><span data-stu-id="2ac96-122">Category</span></span>

- <span data-ttu-id="2ac96-123">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ac96-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ac96-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="2ac96-124">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
