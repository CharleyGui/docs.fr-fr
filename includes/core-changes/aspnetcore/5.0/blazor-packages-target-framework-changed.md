---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416246"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a>Éblouissante : version cible du .NET Framework des packages NuGet modifiée

Les projets de webassembly éblouissants 3,2 ont été compilés pour cibler .NET Standard 2,1 ( `<TargetFramework>netstandard2.1</TargetFramework>` ). Dans ASP.NET Core 5,0, les projets de serveur éblouissant et de webassembly éblouissant ciblent .NET 5,0 ( `<TargetFramework>net5.0</TargetFramework>` ). Pour mieux s’aligner sur la modification de la version cible de .NET Framework, les packages éblouissants suivants ne ciblent plus .NET Standard 2,1 :

* [Microsoft. AspNetCore. Components](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [Microsoft. AspNetCore. Components. Authorization](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [Microsoft. AspNetCore. Components. Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [Microsoft. AspNetCore. Components. Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [Microsoft. AspNetCore. Components. webassembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [Microsoft. AspNetCore. Components. webassembly. Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSInterop](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop. webassembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [Microsoft. Authentication. webassembly. MSAL](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 7

#### <a name="old-behavior"></a>Ancien comportement

Dans éblouissant 3,1 et 3,2, les packages ciblent .NET Standard 2,1 et .NET Core 3,1.

#### <a name="new-behavior"></a>Nouveau comportement

Dans ASP.NET Core 5,0, les packages ciblent .NET 5,0.

#### <a name="reason-for-change"></a>Motif de modification

La modification a été apportée pour mieux s’adapter aux exigences de .NET Target Framework.

#### <a name="recommended-action"></a>Action recommandée

Les projets de webassembly éblouissants 3,2 doivent cibler .NET 5,0 dans le cadre de la mise à jour de leurs références de package à 5. x.x. Les bibliothèques qui font référence à l’un de ces packages peuvent cibler .NET 5,0 ou plusieurs cibles en fonction de leurs besoins.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!--

#### Affected APIs

Not detectable via API analysis

-->
