---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365643"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a>La prise en charge intégrée de WinRT est supprimée de .NET

La prise en charge intégrée de la consommation des API [Windows Runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) dans .net est supprimée.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 6

#### <a name="change-description"></a>Description de la modification

Auparavant, CoreCLR pouvait consommer des [fichiers de métadonnées Windows (WinMD)](/uwp/winrt-cref/winmd-files) pour l’activité et l’utilisation des types WinRT. À compter de .NET 5,0, CoreCLR ne peut plus consommer les fichiers WinMD directement.

Si vous tentez de référencer un assembly non pris en charge, vous obtiendrez un <xref:System.IO.FileNotFoundException> . Si vous activez une classe WinRT, vous obtenez un <xref:System.PlatformNotSupportedException> .

Cette modification avec rupture a été effectuée pour les raisons suivantes :

- Par conséquent, WinRT peut être développé et amélioré séparément du Runtime .NET.
- Pour la symétrie avec les systèmes d’interopérabilité fournis pour d’autres systèmes d’exploitation, tels que iOS et Android.
- Pour tirer parti d’autres fonctionnalités .NET, telles que les fonctionnalités C#, la liaison de langage intermédiaire (IL) et la compilation à l’avance (AOA).
- Pour simplifier le code base du Runtime .NET.

#### <a name="recommended-action"></a>Action recommandée

- Supprimez les références au [package Microsoft. Windows. Sdk. Contracts](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) et remplacez-les par des références au [package Microsoft.Windows.Sdk.net](https://www.nuget.org/packages/microsoft.windows.sdk.net).

- Utilisez la chaîne de l’outil [C#/WinRT](/windows/uwp/csharp-winrt/) pour générer ou personnaliser les types et les API WinRT dans .net 5,0 et versions ultérieures.

#### <a name="category"></a>Category

Interop

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
