---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237843"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en `localhost` échoue

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6 et 4.6.1, une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en <code>localhost</code> échoue avec l’erreur &quot;Une erreur liée au réseau ou spécifique à l’instance s’est produite lors de l’établissement d’une connexion à SQL Server. Le serveur est introuvable ou inaccessible. Vérifiez que le nom de l’instance est correct et que SQL Server est configuré pour autoriser les connexions à distance. (fournisseur : interfaces réseau SQL, erreur : 26 - Erreur lors de la localisation du serveur/de l’instance spécifiés)&quot;|
|Suggestion|Ce problème a été résolu et le comportement précédent a été restauré dans .NET Framework 4.6.2. Pour vous connecter à une base de données SQL Server qui se résout en <code>localhost</code>, effectuez une mise à niveau vers .NET Framework 4.6.2.|
|Étendue|Secondaire|
|Version|4.6|
|Type|Runtime|
