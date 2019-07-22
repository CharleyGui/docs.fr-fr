---
ms.openlocfilehash: fe6ff59066c9e6bcf5387e7c266c879b8ae173c6
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237681"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>Le paramètre d’application « dataAnnotations:dataTypeAttribute:disableRegEx » est activé par défaut dans .NET Framework 4.7.2

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6.1, un paramètre d’application (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) a été introduit pour permettre aux utilisateurs de désactiver l’utilisation d’expressions régulières dans les attributs de type de données (tels que <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> et <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Et ainsi de réduire les vulnérabilités de sécurité, comme empêcher la possibilité d’une attaque par déni de Service avec des expressions régulières spécifiques.<br/>Dans .NET Framework 4.6.1, ce paramètre d’application pour désactiver l’utilisation de RegEx a été défini sur <code>false</code> par défaut. À compter de .NET Framework 4.7.2, ce commutateur de configuration est défini sur <code>true</code> par défaut afin de réduire davantage les vulnérabilités de sécurité pour les applications web qui ciblent .NET Framework 4.7.2 et ultérieur.|
|Suggestion|Si vous trouvez que les expressions régulières de votre application web ne fonctionnent pas après la mise à niveau vers .NET Framework 4.7.2, vous pouvez mettre à jour la valeur du paramètre <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> sur <code>false</code> pour revenir au comportement précédent.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Mineur|
|Version|4.7.2|
|Type|Runtime|
