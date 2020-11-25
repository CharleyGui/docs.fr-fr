---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032515"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hébergement : types IHostingEnvironment et IApplicationLifetime marqués comme obsolètes et remplacés

De nouveaux types ont été introduits pour remplacer `IHostingEnvironment` les types et existants `IApplicationLifetime` .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Il existe deux `IHostingEnvironment` types différents et `IApplicationLifetime` de `Microsoft.Extensions.Hosting` et `Microsoft.AspNetCore.Hosting` .

#### <a name="new-behavior"></a>Nouveau comportement

Les anciens types ont été marqués comme obsolètes et remplacés par de nouveaux types.

#### <a name="reason-for-change"></a>Motif de modification

Quand `Microsoft.Extensions.Hosting` a été introduit dans ASP.NET Core 2,1, certains types comme `IHostingEnvironment` et `IApplicationLifetime` ont été copiés à partir de `Microsoft.AspNetCore.Hosting` . Certaines modifications de l’ASP.NET Core 3,0 entraînent l’inclusion des espaces de noms et dans les applications `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` . Toute utilisation de ces types dupliqués provoque une erreur du compilateur « référence ambiguë » lorsque les deux espaces de noms sont référencés.

#### <a name="recommended-action"></a>Action recommandée

Remplacement des utilisations des anciens types par les types nouvellement introduits comme indiqué ci-dessous :

**Types obsolètes (avertissement) :**

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

**Nouveaux types :**

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

Les nouvelles `IHostEnvironment` `IsDevelopment` méthodes et les `IsProduction` méthodes d’extension se trouvent dans l' `Microsoft.Extensions.Hosting` espace de noms. Cet espace de noms devra peut-être être ajouté à votre projet.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
