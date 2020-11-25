---
title: 'Modification avec rupture : thread. Abort est obsolète'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où les API Thread. Abort sont obsolètes.
ms.date: 11/01/2020
ms.openlocfilehash: 6d7dfce8fda393bfd88c9b4cf0c59d53942cee25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760872"
---
# <a name="threadabort-is-obsolete"></a><span data-ttu-id="ff721-103">Thread. Abort est obsolète</span><span class="sxs-lookup"><span data-stu-id="ff721-103">Thread.Abort is obsolete</span></span>

<span data-ttu-id="ff721-104">Les <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="ff721-104">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="ff721-105">Les projets qui ciblent .NET 5,0 ou une version ultérieure rencontreront un avertissement au moment de la compilation `SYSLIB0006` si ces méthodes sont appelées.</span><span class="sxs-lookup"><span data-stu-id="ff721-105">Projects that target .NET 5.0 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

## <a name="change-description"></a><span data-ttu-id="ff721-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ff721-106">Change description</span></span>

<span data-ttu-id="ff721-107">Auparavant, les appels à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ne produisaient pas d’avertissements au moment de la compilation, mais la méthode avait levé une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ff721-107">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="ff721-108">À compter de .NET 5,0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> est marqué comme obsolète en tant qu’avertissement.</span><span class="sxs-lookup"><span data-stu-id="ff721-108">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="ff721-109">L’appel de cette méthode génère un avertissement du compilateur `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="ff721-109">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="ff721-110">L’implémentation de la méthode est inchangée et continue à lever une <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="ff721-110">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ff721-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="ff721-111">Reason for change</span></span>

<span data-ttu-id="ff721-112">Étant donné que <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> lève toujours une <xref:System.PlatformNotSupportedException> sur toutes les implémentations de .net, à l’exception de .NET Framework, <xref:System.ObsoleteAttribute> a été ajouté à la méthode pour attirer l’attention sur les endroits où elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="ff721-112">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ff721-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ff721-113">Version introduced</span></span>

<span data-ttu-id="ff721-114">5.0</span><span class="sxs-lookup"><span data-stu-id="ff721-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ff721-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ff721-115">Recommended action</span></span>

- <span data-ttu-id="ff721-116">Utilisez un <xref:System.Threading.CancellationToken> pour abandonner le traitement d’une unité de travail au lieu d’appeler <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ff721-116">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ff721-117">L’exemple suivant illustre l’utilisation de <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="ff721-117">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

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

  <span data-ttu-id="ff721-118">Pour plus d’informations, consultez [Annulation dans les threads managés](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="ff721-118">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="ff721-119">Pour supprimer l’avertissement au moment de la compilation, supprimez le code d’avertissement `SYSLIB0006` .</span><span class="sxs-lookup"><span data-stu-id="ff721-119">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="ff721-120">Le code d’avertissement est spécifique à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> et sa suppression ne supprime pas les autres avertissements obsoletion dans votre code.</span><span class="sxs-lookup"><span data-stu-id="ff721-120">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="ff721-121">Toutefois, nous vous recommandons de supprimer les appels au <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> au lieu de supprimer l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="ff721-121">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="ff721-122">Vous pouvez également supprimer l’avertissement dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ff721-122">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a><span data-ttu-id="ff721-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="ff721-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
