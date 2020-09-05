---
ms.openlocfilehash: ed669364efe9dd8f57d831a3764dd3fc68cd5e05
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497017"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>La mauvaise gestion multipartite d’ASP.NET peut entraîner la perte de données de formulaire.

#### <a name="details"></a>Détails

Dans les applications qui ciblent .NET Framework 4.7.2 et versions antérieures, ASP.Net risque de mal analyser les valeurs limites multipartites, ce qui entraîne l’indisponibilité de données de formulaire pendant l’exécution de la requête. Les applications qui ciblent .NET Framework 4.8 ou versions ultérieures analysent correctement les données multipartites pour que les valeurs de formulaire soient disponibles lors de l’exécution de la requête.

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
