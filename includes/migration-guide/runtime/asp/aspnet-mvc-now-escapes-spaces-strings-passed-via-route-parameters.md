---
ms.openlocfilehash: afbf34710c75d0f0586ddfdb2e7937d8d76d5399
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497572"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC place désormais dans une séquence d’échappement les espaces dans les chaînes passées via des paramètres d’itinéraire

#### <a name="details"></a>Détails

Pour des raisons de conformité à la norme RFC 2396, les espaces situés dans les itinéraires de routage sont désormais échappés lors du remplissage des paramètres d’action à partir d’un itinéraire. Dans les versions précédentes, <code>/controller/action/some data</code> correspondait à l’itinéraire <code>/controller/action/{data}</code> et fournissait <code>some data</code> comme paramètre de données. Désormais, il fournit <code>some%20data</code> à la place.

#### <a name="suggestion"></a>Suggestion

Le code doit être mis à jour pour ne plus échapper les paramètres de chaîne à partir d’un itinéraire. Si l’URI d’origine est nécessaire, vous pouvez y accéder avec l’API <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)>

<!--

#### Affected APIs

- `M:System.Web.Mvc.RouteAttribute.#ctor(System.String)`

-->
