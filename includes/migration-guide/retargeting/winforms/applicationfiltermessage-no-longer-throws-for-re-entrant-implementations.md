---
ms.openlocfilehash: 8a1e2ca0790cb62e3c2c879f2ba0bb169ef07d77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804345"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage ne lève plus d’exception pour les implémentations réentrantes d’IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Détails|Avant .NET Framework 4.6.1, le fait d’appeler <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> avec un <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> qui appelait <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> ou <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (tout en appelant également <xref:System.Windows.Forms.Application.DoEvents>) levait une exception <xref:System.IndexOutOfRangeException?displayProperty=name>.<p/>Dans les applications qui ciblent le .NET Framework 4.6.1, cette exception n’est plus levée, et des filtres réentrants comme ceux décrits plus haut peuvent être utilisés.|
|Suggestion|Sachez que <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> ne lève plus d’exception pour le comportement <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> réentrant décrit ci-dessus. Ce changement affecte uniquement les applications qui ciblent le .NET Framework 4.6.1. Ces applications peuvent refuser ce changement (tandis que celles qui ciblent des versions antérieures du .NET Framework peuvent l’accepter) à l’aide du commutateur de compatibilité [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation).|
|Étendue|Edge|
|Version|4.6.1|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|
