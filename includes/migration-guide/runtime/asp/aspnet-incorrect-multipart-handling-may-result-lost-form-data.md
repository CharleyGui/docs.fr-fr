---
ms.openlocfilehash: d61a3b3dd855d783d7bff7cb74e5b84969e60860
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608044"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>La mauvaise gestion multipartite d’ASP.NET peut entraîner la perte de données de formulaire.

#### <a name="details"></a>Détails

Dans les applications qui ciblent .NET Framework 4.7.2 et les versions antérieures, ASP.NET peut analyser de manière incorrecte des valeurs limites en plusieurs parties, ce qui entraîne l’indisponibilité des données de formulaire lors de l’exécution de la requête. Les applications qui ciblent .NET Framework 4.8 ou versions ultérieures analysent correctement les données multipartites pour que les valeurs de formulaire soient disponibles lors de l’exécution de la requête.

#### <a name="suggestion"></a>Suggestion

À compter des applications qui s’exécutent sur .NET Framework 4.8, quand vous ciblez .NET Framework 4.8 ou ultérieur à l’aide de l’élément <code>targetFrameworkVersion</code>, le comportement par défaut change pour supprimer les délimiteurs. Lorsque vous ciblez les versions précédentes du Framework ou que vous n’utilisez pas <code>targetFrameworkVersion</code>, les délimiteurs de fin de certaines valeurs sont toujours retournés. Ce comportement peut aussi être contrôlé explicitement avec un <code>appSetting</code> :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Unknown|
|Version|4.8|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
