---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325238"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a>IIS : les chaînes de requête d’intergiciel UrlRewrite sont conservées

Un défaut d’intergiciel (middleware) IIS UrlRewrite a empêché la conservation de la chaîne de requête dans les règles de réécriture. Ce défaut a été résolu pour maintenir la cohérence avec le comportement du module UrlRewrite IIS.

Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).

#### <a name="version-introduced"></a>Version introduite

ASP.NET Core 5,0 Preview 7

#### <a name="old-behavior"></a>Ancien comportement

Examinez la règle de réécriture suivante :

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

La règle précédente n’ajoute pas la chaîne de requête. Un URI comme `/about?id=1` redirige vers `/contact` au lieu de `/contact?id=1` . L' `appendQueryString` attribut a également la valeur par défaut `true` .

#### <a name="new-behavior"></a>Nouveau comportement

La chaîne de requête est conservée. L’URI de l’exemple dans l' [ancien comportement](#old-behavior) est `/contact?id=1` .

#### <a name="reason-for-change"></a>Motif de modification

L’ancien comportement ne correspondait pas au comportement du module UrlRewrite IIS. Pour prendre en charge le portage entre l’intergiciel et le module, l’objectif est de maintenir des comportements cohérents.

#### <a name="recommended-action"></a>Action recommandée

Si le comportement de la suppression de la chaîne de requête est recommandé, affectez à l’élément la valeur `action` `appendQueryString="false"` .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
