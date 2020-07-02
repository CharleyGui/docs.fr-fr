---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621966"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName n’est pas NULL lors de l’utilisation d’un DataAnnotations.ValidationAttribute personnalisé

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.2 et versions antérieures, quand vous utilisez un <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personnalisé, la propriété <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retourne `null`. Dans .NET Framework version 4,8 antérieure à la mise à jour du 2019 d’octobre, elle retourne le nom du membre. À compter de [.NET Framework version préliminaire du correctif cumulatif pour .NET Framework 4,8 d’octobre 2019](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) , elle retourne `null` par défaut, mais vous pouvez choisir de retourner le nom du membre à la place.

#### <a name="suggestion"></a>Suggestion

Ajoutez le paramètre suivant à votre fichier *web.config* pour que la propriété retourne le nom du membre dans [2019 .NET Framework version préliminaire du cumul de qualité](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pour .NET Framework 4,8 et versions ultérieures.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Dans .NET Framework version 4,8 antérieure à la mise à jour du 2019 d’octobre, l’ajout de ce à votre fichier *web.config* restaure le comportement précédent et la propriété retourne `null` .

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Unknown|
|Version|4.8|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
