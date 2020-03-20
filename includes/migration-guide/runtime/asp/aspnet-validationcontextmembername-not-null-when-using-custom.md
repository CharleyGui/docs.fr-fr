---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77466042"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName n’est pas NULL lors de l’utilisation d’un DataAnnotations.ValidationAttribute personnalisé

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.7.2 et versions antérieures, quand vous utilisez un <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personnalisé, la propriété <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retourne `null`. Dans la version .NET Framework 4.8 avant la mise à jour d’octobre 2019, il renvoie le nom du membre. À partir [de .NET Framework Octobre 2019 Aperçu de la qualité Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pour .NET Framework 4.8, il revient `null` par défaut, mais vous pouvez opter pour retourner le nom du membre à la place. |
|Suggestion|Ajoutez le paramètre suivant à votre fichier *web.config* pour la propriété pour retourner le nom du membre dans [.NET Framework Octobre 2019 Aperçu de la qualité Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pour .NET Framework 4.8 et les versions ultérieures:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Dans la version .NET Framework 4.8 avant la mise à jour d’octobre 2019, ajoutant `null`ceci à votre fichier *web.config* restaure le comportement précédent et les déclarations de propriété.|
|Étendue|Unknown|
|Version|4.8|
|Type|Runtime|
|API affectées|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
