---
ms.openlocfilehash: e605e0f2636d83745815ec4ed27bf72692f18d15
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802681"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>Correctif ASP.NET sur la gestion de InputAttributes et LabelAttributes du contrôle WebForms CheckBox

|   |   |
|---|---|
|Détails|Pour les applications qui ciblent .NET Framework 4.7.2 et versions antérieures, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> qui sont ajoutés programmatiquement à un contrôle <xref:System.Web.UI.WebControls.CheckBox> WebForms sont perdus après la publication (postback). Pour les applications qui ciblent .NET Framework 4.8 ou versions ultérieures, ils sont conservés après la publication (postback).|
|Suggestion|Pour obtenir le bon comportement de restauration des attributs lors de la publication (postback), définissez <code>targetFrameworkVersion</code> sur 4.8 ou ultérieur. Par exemple :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>La définir avec une version antérieure ou ne pas la définir du tout revient à conserver l’ancien comportement incorrect.|
|Portée|Inconnu|
|Version|4.8|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|

