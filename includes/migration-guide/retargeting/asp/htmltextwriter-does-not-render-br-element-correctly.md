---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615651"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter n’affiche pas correctement l’élément `<br/>`

#### <a name="details"></a>Détails

À partir de .NET Framework 4.6, l’appel de <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> et de <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> avec un élément `<BR />` insère correctement un seul `<BR />` (au lieu de deux)

#### <a name="suggestion"></a>Suggestion

Si une application dépendait de la balise `<BR />` supplémentaire, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> doit être appelé une deuxième fois. Notez que ce changement de comportement affecte uniquement les applications qui ciblent .NET Framework 4.6 ou les versions ultérieures. Vous pouvez donc également cibler une version antérieure du .NET Framework pour obtenir l’ancien comportement.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
