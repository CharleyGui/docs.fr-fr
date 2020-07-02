---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619919"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>La propriété HttpRequest.ContentEncoding interdit UTF7

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, l’encodage UTF-7 est interdit dans le corps des <xref:System.Web.HttpRequest?displayProperty=fullName>. Les données des applications qui dépendent des données UTF-7 entrantes ne seront pas décodées correctement dans certains cas.

#### <a name="suggestion"></a>Suggestion

Dans l’idéal, les applications doivent être mises à jour pour ne pas utiliser l’encodage UTF-7 dans les <xref:System.Web.HttpRequest?displayProperty=fullName>. Vous pouvez aussi restaurer le comportement hérité à l’aide de l’attribut <code>aspnet:AllowUtf7RequestContentEncoding</code> de l’élément [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md).

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
