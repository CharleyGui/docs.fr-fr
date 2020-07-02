---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620052"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Les codes d’erreur pour maxRequestLength ou maxReceivedMessageSize sont différents

#### <a name="details"></a>Détails

Les messages dans les services web WCF hébergés dans les services IIS (Internet Information Services) ou sur le serveur de développement ASP.NET qui dépassent maxRequestLength (dans ASP.NET) ou maxReceivedMessageSize (dans WCF) ont un code d’erreur différent. Le code d’état HTTP est passé de 400 (Demande incorrecte) à 413 (Entité de demande trop grande), et les messages qui dépassent le paramètre maxRequestLength ou maxReceivedMessageSize lèvent une exception <xref:System.ServiceModel.ProtocolException?displayProperty=fullName>. Cela inclut les cas dans lesquels le mode de transfert est Transmis en continu.

#### <a name="suggestion"></a>Suggestion

Cette modification facilite le débogage dans les cas où la longueur du message dépasse les limites autorisées par ASP.NET ou WCF. Vous devez modifier tout code qui effectue un traitement en fonction d’un code d’état HTTP 400.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|
