---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621976"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>Correctif ASP.NET sur la gestion de InputAttributes et LabelAttributes du contrôle WebForms CheckBox

#### <a name="details"></a>Détails

Pour les applications qui ciblent .NET Framework 4.7.2 et versions antérieures, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> qui sont ajoutés programmatiquement à un contrôle <xref:System.Web.UI.WebControls.CheckBox> WebForms sont perdus après la publication (postback). Pour les applications qui ciblent .NET Framework 4.8 ou versions ultérieures, ils sont conservés après la publication (postback).

#### <a name="suggestion"></a>Suggestion

Pour obtenir le bon comportement de restauration des attributs lors de la publication (postback), définissez <code>targetFrameworkVersion</code> sur 4.8 ou ultérieur. Par exemple :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>La définir avec une version antérieure ou ne pas la définir du tout revient à conserver l’ancien comportement incorrect.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Unknown|
|Version|4.8|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
