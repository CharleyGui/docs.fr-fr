---
title: AVERTISSEMENT SYSLIB0004
description: En savoir plus sur les obsoletions qui génèrent un avertissement au moment de la compilation SYSLIB0004.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: f48fd8915a13f9f99b091eca895dcd74a8f18907
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440716"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a>SYSLIB0004 : la fonctionnalité de région d’exécution limitée n’est pas prise en charge

La fonctionnalité des [régions d’exécution limitée (CER)](../../framework/performance/constrained-execution-regions.md) est prise en charge uniquement dans .NET Framework. Par conséquent, diverses API relatives à CER sont marquées comme obsolètes, à partir de .NET 5,0. L’utilisation de ces API génère un avertissement `SYSLIB0004` au moment de la compilation.

Les API CER suivantes sont obsolètes :

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="workarounds"></a>Solutions de contournement

- Si vous avez appliqué un attribut CER à une méthode, supprimez l’attribut. Ces attributs n’ont aucun effet dans .NET 5,0 et versions ultérieures.

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

- Si vous appelez `RuntimeHelpers.ProbeForSufficientStack` ou `RuntimeHelpers.PrepareContractedDelegate` , supprimez l’appel. Ces appels n’ont aucun effet dans .NET 5,0 et versions ultérieures.

  ```csharp
  public void DoSomething()
  {
      // REMOVE the call below.
      RuntimeHelpers.ProbeForSufficientStack();

      // (Remainder of your method logic here.)
  }
  ```

- Si vous appelez `RuntimeHelpers.PrepareConstrainedRegions` , supprimez l’appel. Cet appel n’a aucun effet dans .NET 5,0 et versions ultérieures.

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

- Si vous appelez `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup` , remplacez l’appel par un bloc _try/catch/finally_ standard.

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Voir aussi

- [Régions d’exécution restreintes](../../framework/performance/constrained-execution-regions.md)
