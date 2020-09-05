---
ms.openlocfilehash: a84d72813a46d6bb39f4710b35d2c9dc859e30ef
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497874"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>L’événement Page.LoadComplete n’entraîne plus l’appel d’une liaison de données par le contrôle System.Web.UI.WebControls.EntityDataSource

#### <a name="details"></a>Détails

L'événement <xref:System.Web.UI.Page.LoadComplete> ne force plus le contrôle <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> à appeler une liaison de données pour les modifications dans le but de créer/mettre à jour/supprimer des paramètres. Cette modification supprime un aller-retour superflu vers la base de données, empêche la réinitialisation des valeurs des contrôles et produit un comportement cohérent avec les autres contrôles de données, tels que <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> et <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>. Elle produit un comportement différent dans le cas peu probable où les applications dépendraient de l'appel de la liaison de données dans l'événement <xref:System.Web.UI.Page.LoadComplete>.

#### <a name="suggestion"></a>Suggestion

Si une liaison de données est nécessaire, appelez manuellement la méthode databind dans un événement situé plus haut dans la publication (postback).

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
