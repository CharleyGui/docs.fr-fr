---
ms.openlocfilehash: 9bf6972812bdf4a385b99fe34d2cd3cd8a91c8cf
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804431"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce prend en charge SHA-256 sur les applications ciblées par la version 4.0

|   |   |
|---|---|
|Détails|Avant, une application ClickOnce disposant d’un certificat signé avec SHA-256 nécessitait la présence de .NET Framework 4.5 ou ultérieur, même si l’application ciblait la version 4.0. Désormais, les applications ClickOnce ciblées par .NET Framework 4.0 peuvent s’exécuter sur .NET Framework 4.0, même si elles sont signées avec SHA-256.|
|Suggestion|Ce changement supprime cette dépendance et permet aux certificats SHA-256 d’être utilisés pour signer des applications ClickOnce qui ciblent .NET Framework 4 et les versions antérieures.|
|Portée|Mineur|
|Version|4.6|
|Type|Reciblage|

