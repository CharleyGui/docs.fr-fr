---
ms.openlocfilehash: ee67b32b093ebd42f8ac685b34b12f2f6833be86
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332919"
---
### <a name="threadabort-is-obsolete"></a>Thread. Abort est obsolète

Les <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> API sont obsolètes. Les projets qui ciblent .NET 5,0 ou une version ultérieure rencontreront un avertissement au moment de la compilation `SYSLIB0006` si ces méthodes sont appelées.

#### <a name="change-description"></a>Description de la modification

Auparavant, les appels à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ne produisaient pas d’avertissements au moment de la compilation, mais la méthode avait levé une <xref:System.PlatformNotSupportedException> au moment de l’exécution.

À compter de .NET 5,0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> est marqué comme obsolète en tant qu’avertissement. L’appel de cette méthode génère un avertissement du compilateur `SYSLIB0006` . L’implémentation de la méthode est inchangée et continue à lever une <xref:System.PlatformNotSupportedException> .

#### <a name="reason-for-change"></a>Motif de modification

Étant donné que <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> lève toujours une <xref:System.PlatformNotSupportedException> sur toutes les implémentations de .net, à l’exception de .NET Framework, <xref:System.ObsoleteAttribute> a été ajouté à la méthode pour attirer l’attention sur les endroits où elle est appelée.

#### <a name="version-introduced"></a>Version introduite

5,0 RC 1

#### <a name="recommended-action"></a>Action recommandée

- Utilisez un <xref:System.Threading.CancellationToken> pour abandonner le traitement d’une unité de travail au lieu d’appeler <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> . L’exemple suivant illustre l’utilisation de <xref:System.Threading.CancellationToken> .

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

  Pour plus d’informations, consultez [Annulation dans les threads managés](../../../../docs/standard/threading/cancellation-in-managed-threads.md).

- Pour supprimer l’avertissement au moment de la compilation, supprimez le code d’avertissement `SYSLIB0006` . Le code d’avertissement est spécifique à <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> et sa suppression ne supprime pas les autres avertissements obsoletion dans votre code. Toutefois, nous vous recommandons de supprimer les appels au <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> au lieu de supprimer l’avertissement.

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  Vous pouvez également supprimer l’avertissement dans le fichier projet.

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

#### <a name="category"></a>Category

- Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
