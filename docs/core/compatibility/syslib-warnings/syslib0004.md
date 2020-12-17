---
title: AVERTISSEMENT SYSLIB0004
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0004.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 03be8bb54f71f74ed94ee2c3f8489397ae1e99b5
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596496"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="c0d41-103">SYSLIB0004 : la fonctionnalité de région d’exécution limitée n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="c0d41-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="c0d41-104">La fonctionnalité des [régions d’exécution limitée (CER)](../../../framework/performance/constrained-execution-regions.md) est prise en charge uniquement dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0d41-104">The [Constrained execution regions (CER)](../../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="c0d41-105">Par conséquent, diverses API relatives à CER sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="c0d41-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="c0d41-106">L’utilisation de ces API génère un avertissement `SYSLIB0004` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c0d41-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="c0d41-107">Les API CER suivantes sont obsolètes :</span><span class="sxs-lookup"><span data-stu-id="c0d41-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="c0d41-108">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="c0d41-108">Workarounds</span></span>

- <span data-ttu-id="c0d41-109">Si vous avez appliqué un attribut CER à une méthode, supprimez l’attribut.</span><span class="sxs-lookup"><span data-stu-id="c0d41-109">If you have applied a CER attribute to a method, remove the attribute.</span></span> <span data-ttu-id="c0d41-110">Ces attributs n’ont aucun effet dans .NET 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c0d41-110">These attributes have no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  // REMOVE the attribute below.
  [ReliabilityContract(Consistency.WillNotCorruptState, Cer.Success)]
  public void DoSomething()
  {
  }

  // REMOVE the attribute below.
  [PrePrepareMethod]
  public void DoSomething()
  {
  }
  ```

- <span data-ttu-id="c0d41-111">Si vous appelez `RuntimeHelpers.ProbeForSufficientStack` ou `RuntimeHelpers.PrepareContractedDelegate` , supprimez l’appel.</span><span class="sxs-lookup"><span data-stu-id="c0d41-111">If you are calling `RuntimeHelpers.ProbeForSufficientStack` or `RuntimeHelpers.PrepareContractedDelegate`, remove the call.</span></span> <span data-ttu-id="c0d41-112">Ces appels n’ont aucun effet dans .NET 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c0d41-112">These calls have no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  public void DoSomething()
  {
      // REMOVE the call below.
      RuntimeHelpers.ProbeForSufficientStack();

      // (Remainder of your method logic here.)
  }
  ```

- <span data-ttu-id="c0d41-113">Si vous appelez `RuntimeHelpers.PrepareConstrainedRegions` , supprimez l’appel.</span><span class="sxs-lookup"><span data-stu-id="c0d41-113">If you are calling `RuntimeHelpers.PrepareConstrainedRegions`, remove the call.</span></span> <span data-ttu-id="c0d41-114">Cet appel n’a aucun effet dans .NET 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c0d41-114">This call has no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  public void DoSomething_Old()
  {
      // REMOVE the call below.
      RuntimeHelpers.PrepareConstrainedRegions();
      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }

  public void DoSomething_Corrected()
  {
      // There is no call to PrepareConstrainedRegions. It's a normal try / finally block.

      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

- <span data-ttu-id="c0d41-115">Si vous appelez `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup` , remplacez l’appel par un bloc _try/catch/finally_ standard.</span><span class="sxs-lookup"><span data-stu-id="c0d41-115">If you are calling `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup`, replace the call with a standard _try / catch / finally_ block.</span></span>

  ```csharp
  // The sample below produces warning SYSLIB0004.
  public void DoSomething_Old()
  {
      RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(MyTryCode, MyCleanupCode, null);
  }
  public void MyTryCode(object state) { /* try code */ }
  public void MyCleanupCode(object state, bool exceptionThrown) { /* cleanup code */ }

  // The corrected sample below does not produce warning SYSLIB0004.
  public void DoSomething_Corrected()
  {
      try
      {
          // try code
      }
      catch (Exception ex)
      {
          // exception handling code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="c0d41-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0d41-116">See also</span></span>

- [<span data-ttu-id="c0d41-117">Régions d’exécution restreintes</span><span class="sxs-lookup"><span data-stu-id="c0d41-117">Constrained execution regions</span></span>](../../../framework/performance/constrained-execution-regions.md)