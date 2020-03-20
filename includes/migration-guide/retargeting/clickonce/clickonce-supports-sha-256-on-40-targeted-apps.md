---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804431"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce prend en charge SHA-256 sur les applications ciblées par la version 4.0

|   |   |
|---|---|
|Détails|Avant, une application ClickOnce disposant d’un certificat signé avec SHA-256 nécessitait la présence de .NET Framework 4.5 ou ultérieur, même si l’application ciblait la version 4.0. Désormais, les applications ClickOnce ciblées par .NET Framework 4.0 peuvent s’exécuter sur .NET Framework 4.0, même si elles sont signées avec SHA-256.|
|Suggestion|Ce changement supprime cette dépendance et permet aux certificats SHA-256 d’être utilisés pour signer des applications ClickOnce qui ciblent .NET Framework 4 et les versions antérieures.|
|Étendue|Secondaire|
|Version|4.6|
|Type|Reciblage|
