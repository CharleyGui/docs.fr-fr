---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394330"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hébergement : types IHostingEnvironment et IApplicationLifetime marqués comme obsolètes et remplacés

De nouveaux types ont été introduits pour `IHostingEnvironment` remplacer `IApplicationLifetime` les types et existants.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Il existe deux types `IHostingEnvironment` différents `IApplicationLifetime` et de `Microsoft.Extensions.Hosting` et `Microsoft.AspNetCore.Hosting`.

#### <a name="new-behavior"></a>Nouveau comportement

Les anciens types ont été marqués comme obsolètes et remplacés par de nouveaux types.

#### <a name="reason-for-change"></a>Motif de modification

Quand `Microsoft.Extensions.Hosting` a été introduit dans ASP.net Core 2,1, certains types `IHostingEnvironment` comme `IApplicationLifetime` et ont été `Microsoft.AspNetCore.Hosting`copiés à partir de. Certaines modifications de l’ASP.NET Core 3,0 entraînent l’inclusion `Microsoft.Extensions.Hosting` des `Microsoft.AspNetCore.Hosting` espaces de noms et dans les applications. Toute utilisation de ces types dupliqués provoque une erreur du compilateur « référence ambiguë » lorsque les deux espaces de noms sont référencés.

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

Les nouvelles `IHostEnvironment` `IsDevelopment` méthodes `IsProduction` et les méthodes d’extension `Microsoft.Extensions.Hosting` se trouvent dans l’espace de noms. Cet espace de noms devra peut-être être ajouté à votre projet.

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
