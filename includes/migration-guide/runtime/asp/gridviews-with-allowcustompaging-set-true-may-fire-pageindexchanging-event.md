---
ms.openlocfilehash: c9c46793a0f66894649796d960547848ff5ebf8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858447"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>Les contrôles GridView avec la valeur true définie pour AllowCustomPaging peuvent déclencher l’événement PageIndexChanging en quittant la dernière page de la vue

|   |   |
|---|---|
|Détails|Un bogue dans .NET Framework 4.5 contraint parfois <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> à ne pas se déclencher pour les <xref:System.Web.UI.WebControls.GridView?displayProperty=name> qui ont activé <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Suggestion|Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework. Comme solution de contournement, l’application peut effectuer une opération BindGrid explicite sur n’importe quel <code>Page_Load</code> qui répond à ces conditions (le contrôle <xref:System.Web.UI.WebControls.GridView?displayProperty=name> figure dans la dernière page et Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> est différent de <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). L’application peut également être modifiée pour autoriser la pagination (au lieu de la pagination personnalisée), comme ce scénario ne présente pas le problème.|
|Étendue|Secondaire|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
