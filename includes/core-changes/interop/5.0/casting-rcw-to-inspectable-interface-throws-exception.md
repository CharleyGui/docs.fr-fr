---
ms.openlocfilehash: 8693c1fdef5fa194b16127d4f1dd87e23ad68f2d
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438042"
---
### <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a>La conversion du wrapper RCW en `InterfaceIsIInspectable` interface lève PlatformNotSupportedException

Le cast d’un wrapper RCW (Runtime Callable Wrapper) en une interface marquée comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> lève désormais une exception <xref:System.PlatformNotSupportedException> . Ce changement est un suivi de la [Suppression de la prise en charge WinRT de .net](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).

#### <a name="version-introduced"></a>Version introduite

5,0 RC2

#### <a name="change-description"></a>Description de la modification

Dans les versions .NET antérieures à .NET 5,0 Preview 6, le fait de convertir un wrapper RCW en une interface marquée comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> fonctionnait comme prévu. Dans .NET 5,0 préversions 6-8 et RC1, vous pouvez réussir le cast d’un wrapper RCW en <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface. Toutefois, vous pouvez obtenir des violations d’accès lorsque vous exécutez des méthodes sur l’interface, car la prise en charge sous-jacente dans le runtime [a été supprimée dans .net 5,0 Preview 6](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).

Dans .NET 5,0 RC2 et versions ultérieures, le cast d’un wrapper RCW en une interface marquée comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> lève une <xref:System.PlatformNotSupportedException> au moment de la conversion.

#### <a name="reason-for-change"></a>Motif de modification

La prise en charge de <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> a été [supprimée dans une version précédente de .net 5,0 Preview](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net). Toutefois, une conversion vers une <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface a été accidentellement négligée. Étant donné que la prise en charge sous-jacente dans le runtime n’existe plus, la levée d’un <xref:System.PlatformNotSupportedException> permet d’obtenir un chemin d’échec normal. La levée d’une exception rend également plus détectable que cette fonctionnalité n’est plus prise en charge.

#### <a name="recommended-action"></a>Action recommandée

- Si vous pouvez définir l’interface dans un fichier de métadonnées Windows Runtime (WinMD), utilisez l’outil C#/WinRT à la place.

- Sinon, marquez l’interface comme <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> au lieu de <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> , puis ajoutez trois entrées factices au début de l’interface pour les <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> méthodes. L’extrait de code suivant montre un exemple.

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

#### <a name="category"></a>Category

Interop

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

-->
