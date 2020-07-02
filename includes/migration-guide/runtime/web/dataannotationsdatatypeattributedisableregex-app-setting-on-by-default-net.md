---
ms.openlocfilehash: f17efc89b738a9fd20cc687de1dae01a44664271
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621098"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>Le paramètre d’application « dataAnnotations:dataTypeAttribute:disableRegEx » est activé par défaut dans .NET Framework 4.7.2

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.1, un paramètre d’application (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) a été introduit pour permettre aux utilisateurs de désactiver l’utilisation d’expressions régulières dans les attributs de type de données (tels que <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> et <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Et ainsi de réduire les vulnérabilités de sécurité, comme empêcher la possibilité d’une attaque par déni de Service avec des expressions régulières spécifiques.<br/>Dans .NET Framework 4.6.1, ce paramètre d’application pour désactiver l’utilisation de RegEx a été défini sur <code>false</code> par défaut. À partir de .NET Framework 4.7.2, ce commutateur de configuration est défini sur <code>true</code> par défaut pour réduire encore davantage la vulnérabilité sécurisée pour les applications Web qui ciblent .NET Framework 4.7.2 et versions ultérieures.

#### <a name="suggestion"></a>Suggestion

Si vous trouvez que les expressions régulières de votre application web ne fonctionnent pas après la mise à niveau vers .NET Framework 4.7.2, vous pouvez mettre à jour la valeur du paramètre <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> sur <code>false</code> pour revenir au comportement précédent.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.7.2|
|Type|Runtime|
