---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466042"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName n’est pas NULL lors de l’utilisation d’un DataAnnotations.ValidationAttribute personnalisé

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.7.2 et versions antérieures, quand vous utilisez un <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personnalisé, la propriété <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retourne `null`. Dans .NET Framework version 4,8 antérieure à la mise à jour du 2019 d’octobre, elle retourne le nom du membre. À compter de [.NET Framework version préliminaire d’octobre 2019](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pour .NET Framework 4,8, elle retourne `null` par défaut, mais vous pouvez choisir de retourner le nom du membre à la place. |
|Suggestion|Ajoutez le paramètre suivant à votre fichier *Web. config* pour que la propriété retourne le nom du membre dans [2019 .NET Framework version préliminaire du cumul de qualité](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) pour .NET Framework 4,8 et versions ultérieures.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Dans .NET Framework version 4,8 antérieure à la mise à jour du 2019 d’octobre, l’ajout de ce à votre fichier *Web. config* rétablit le comportement précédent et la propriété retourne `null`.|
|Étendue|Unknown|
|Version|4.8|
|Type|Runtime|
|API affectées|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
