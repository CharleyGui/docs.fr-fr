---
ms.openlocfilehash: 3b94c88809513e31a5f226bcfce39abbfa4de378
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017370"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName n’est pas NULL lors de l’utilisation d’un DataAnnotations.ValidationAttribute personnalisé

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.7.2 et versions antérieures, quand vous utilisez un <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personnalisé, la propriété <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retourne <code>null</code>.  Dans .NET Framework 4.8, elle retourne le nom du membre.|
|Suggestion|Pour restaurer le comportement précédent, ajoutez le paramètre suivant à votre fichier de configuration d’application :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ce comportement sera modifié dans une prochaine version du service, où vous devrez choisir explicitement le nouveau comportement. La propriété retournera une valeur non null pour un `ValidationAttribute` personnalisé si le commutateur `aspnet:GetValidationMemberName` est défini sur `true`.|
|Portée|Inconnu|
|Version|4.8|
|Type|Runtime|
|API affectées|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
