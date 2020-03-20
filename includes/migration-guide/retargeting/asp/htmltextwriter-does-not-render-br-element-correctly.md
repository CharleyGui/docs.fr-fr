---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804489"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter n’affiche pas correctement l’élément `<br/>`

|   |   |
|---|---|
|Détails|À partir de .NET Framework 4.6, l’appel de <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> et de <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> avec un élément <code>&lt;BR /&gt;</code> insère correctement un seul <code>&lt;BR /&gt;</code> (au lieu de deux)|
|Suggestion|Si une application dépendait de la balise <code>&lt;BR /&gt;</code> supplémentaire, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> doit être appelé une deuxième fois. Notez que ce changement de comportement affecte uniquement les applications qui ciblent .NET Framework 4.6 ou les versions ultérieures. Vous pouvez donc également cibler une version antérieure du .NET Framework pour obtenir l’ancien comportement.|
|Étendue|Edge|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
