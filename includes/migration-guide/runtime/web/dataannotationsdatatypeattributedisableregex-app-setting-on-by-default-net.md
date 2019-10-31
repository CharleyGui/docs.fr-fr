---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085537"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>Le paramètre d’application « dataAnnotations:dataTypeAttribute:disableRegEx » est activé par défaut dans .NET Framework 4.7.2

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6.1, un paramètre d’application (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) a été introduit pour permettre aux utilisateurs de désactiver l’utilisation d’expressions régulières dans les attributs de type de données (tels que <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> et <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Et ainsi de réduire les vulnérabilités de sécurité, comme empêcher la possibilité d’une attaque par déni de Service avec des expressions régulières spécifiques.<br/>Dans .NET Framework 4.6.1, ce paramètre d’application pour désactiver l’utilisation de RegEx a été défini sur <code>false</code> par défaut. À partir de .NET Framework 4.7.2, ce commutateur de configuration est défini sur <code>true</code> par défaut pour réduire encore davantage la vulnérabilité sécurisée pour les applications Web qui ciblent .NET Framework 4.7.2 et versions ultérieures.|
|Suggestion|Si vous trouvez que les expressions régulières de votre application web ne fonctionnent pas après la mise à niveau vers .NET Framework 4.7.2, vous pouvez mettre à jour la valeur du paramètre <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> sur <code>false</code> pour revenir au comportement précédent.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Mineur|
|Version|4.7.2|
|Tapez|Exécution|
