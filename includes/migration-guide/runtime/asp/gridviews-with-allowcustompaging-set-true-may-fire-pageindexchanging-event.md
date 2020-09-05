---
ms.openlocfilehash: 4d210eeedd2f228017634d29f11554deb6ed8079
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497367"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>Les contrôles GridView avec la valeur true définie pour AllowCustomPaging peuvent déclencher l’événement PageIndexChanging en quittant la dernière page de la vue

#### <a name="details"></a>Détails

Un bogue dans .NET Framework 4.5 contraint parfois <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> à ne pas se déclencher pour les <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> qui ont activé <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework. Comme solution de contournement, l’application peut effectuer une opération BindGrid explicite sur n’importe quel <code>Page_Load</code> qui répond à ces conditions (le contrôle <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> figure dans la dernière page et Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> est différent de <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>). L’application peut également être modifiée pour autoriser la pagination (au lieu de la pagination personnalisée), comme ce scénario ne présente pas le problème.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.UI.WebControls.GridView.AllowCustomPaging`

-->
