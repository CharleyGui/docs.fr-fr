---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621788"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en `localhost` échoue

#### <a name="details"></a>Détails

Dans .NET Framework 4.6 et 4.6.1, une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en <code>localhost</code> échoue avec l’erreur &quot;Une erreur liée au réseau ou spécifique à l’instance s’est produite lors de l’établissement d’une connexion à SQL Server. Le serveur est introuvable ou inaccessible. Vérifiez que le nom de l’instance est correct et que SQL Server est configuré pour autoriser les connexions à distance. (fournisseur : interfaces réseau SQL, erreur : 26 - Erreur lors de la localisation du serveur/de l’instance spécifiés)&quot;

#### <a name="suggestion"></a>Suggestion

Ce problème a été résolu et le comportement précédent a été restauré dans .NET Framework 4.6.2. Pour vous connecter à une base de données SQL Server qui se résout en <code>localhost</code>, effectuez une mise à niveau vers .NET Framework 4.6.2.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6|
|Type|Runtime|
