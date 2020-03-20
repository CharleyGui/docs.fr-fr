---
ms.openlocfilehash: da79a19b3276f6fd2d679eb98406dd85e2a19948
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997609"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Les applications publiées avec ClickOnce qui utilisent un certificat de signature de code SHA-256 peuvent échouer sur Windows 2003

|   |   |
|---|---|
|Détails|L'exécutable est signé avec SHA256. Auparavant, il était signé avec SHA1, que le certificat de signature du code ait été SHA-1 ou SHA-256. Cela s’applique aux :<ul><li>Toutes les applications générées avec Visual Studio 2012 ou ultérieur.</li><li>Toutes les applications générées avec Visual Studio 2010 ou antérieur en présence de .NET Framework 4.5.</li></ul>En outre, si .NET Framework 4.5 (ou une version ultérieure) est présent, le manifeste ClickOnce est également signé avec SHA-256 pour les certificats SHA-256, quelle que soit la version du .NET Framework sur laquelle il a été compilé.|
|Suggestion|Le changement de signature de l’exécutable ClickOnce affecte uniquement les systèmes Windows Server 2003. Vous devez installer le correctif logiciel KB 938397. Le changement de signature du manifeste avec l'algorithme SHA-256 même quand une application cible .NET Framework 4.0, ou des versions antérieures, présente une dépendance de runtime sur .NET Framework 4.5 ou version ultérieure.|
|Étendue|Edge|
|Version|4.5|
|Type|Reciblage|
