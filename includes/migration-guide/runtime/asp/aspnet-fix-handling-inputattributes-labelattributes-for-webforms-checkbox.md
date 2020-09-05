---
ms.openlocfilehash: 55a26f1ab27792cbedf3f31b797f37d3f768d51a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496710"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>Correctif ASP.NET sur la gestion de InputAttributes et LabelAttributes du contrôle WebForms CheckBox

#### <a name="details"></a>Détails

Pour les applications qui ciblent .NET Framework 4.7.2 et versions antérieures, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> qui sont ajoutés programmatiquement à un contrôle <xref:System.Web.UI.WebControls.CheckBox> WebForms sont perdus après la publication (postback). Pour les applications qui ciblent .NET Framework 4.8 ou versions ultérieures, ils sont conservés après la publication (postback).

#### <a name="suggestion"></a>Suggestion

Pour obtenir le bon comportement de restauration des attributs lors de la publication (postback), définissez <code>targetFrameworkVersion</code> sur 4.8 ou ultérieur. Par exemple :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>La définir avec une version antérieure ou ne pas la définir du tout revient à conserver l’ancien comportement incorrect.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Unknown|
|Version|4.8|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.UI.WebControls.CheckBox`

-->
