---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394330"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hébergement: IHostingEnvironment et IApplicationLifetime types marqués obsolètes et remplacés

De nouveaux types ont `IHostingEnvironment` été `IApplicationLifetime` introduits pour remplacer les types existants et les types.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Il y `IHostingEnvironment` avait `IApplicationLifetime` deux `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting`différents et les types de et .

#### <a name="new-behavior"></a>Nouveau comportement

Les anciens types ont été marqués comme obsolètes et remplacés par de nouveaux types.

#### <a name="reason-for-change"></a>Raison du changement

Quand `Microsoft.Extensions.Hosting` a été introduit dans ASP.NET Core 2.1, certains types comme `IHostingEnvironment` et `IApplicationLifetime` ont été copiés à partir de `Microsoft.AspNetCore.Hosting`. Certains ASP.NET les modifications de Core 3.0 `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` font que les applications incluent à la fois les espaces nominaux et les noms. Toute utilisation de ces types en double provoque une erreur de compilateur de « référence ambigue » lorsque les deux espaces nom sont référencés.

#### <a name="recommended-action"></a>Action recommandée

Remplacé tous les usages des anciens types avec les types nouvellement introduits comme ci-dessous:

**Types obsolètes (avertissement) :**

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

**Nouveaux types:**

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

Les `IHostEnvironment` `IsDevelopment` nouvelles `IsProduction` méthodes et `Microsoft.Extensions.Hosting` d’extension sont dans l’espace nom. Cet espace de nom peut devoir être ajouté à votre projet.

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
