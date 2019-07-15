---
ms.openlocfilehash: 8ac6d50b192001f6d924b2ffe4a367a33fc2c689
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857587"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en `localhost` échoue

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6 et 4.6.1, une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en <code>localhost</code> échoue avec l’erreur &quot;Une erreur liée au réseau ou spécifique à l’instance s’est produite lors de l’établissement d’une connexion à SQL Server. Le serveur est introuvable ou n’est pas accessible. Vérifiez que le nom de l’instance est correct et que SQL Server est configuré pour autoriser les connexions distantes. (fournisseur : Interfaces réseau SQL, erreur : 26 - Erreur lors de la localisation de Server/Instance spécifié)&quot;|
|Suggestion|Ce problème a été résolu et le comportement précédent a été restauré dans .NET Framework 4.6.2. Pour vous connecter à une base de données SQL Server qui se résout en <code>localhost</code>, effectuez une mise à niveau vers .NET Framework 4.6.2.|
|Portée|Mineur|
|Version|4.6|
|Type|Runtime|

