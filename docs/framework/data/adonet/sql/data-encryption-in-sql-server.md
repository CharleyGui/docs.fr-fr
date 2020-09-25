---
title: Chiffrement des données dans SQL Server
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: d0bda11f1a2933d096aa91d2be79d3af35172284
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169529"
---
# <a name="data-encryption-in-sql-server"></a>Chiffrement des données dans SQL Server

SQL Server fournit des fonctions de chiffrement et déchiffrement de données à l'aide d'un certificat, d'une clé asymétrique ou d'une clé symétrique. Il gère tous ces éléments dans un magasin de certificats interne. Le magasin utilise une hiérarchie de chiffrement qui sécurise les certificats et les clés sur un niveau à l'aide de la couche située au-dessus dans la hiérarchie. Ce domaine de fonctionnalités de SQL Server est appelé stockage secret.  
  
 Le chiffrement à clé symétrique est le mode le plus rapide pris en charge par les fonctions de chiffrement. Ce mode est approprié pour la gestion de volumes importants de données. Les clés symétriques peuvent être chiffrées par des certificats, des mots de passe ou d'autres clés symétriques.  
  
## <a name="keys-and-algorithms"></a>Clés et algorithmes  

 SQL Server prend en charge plusieurs algorithmes de chiffrement à clé symétrique, notamment DES, Triple DES, RC2, RC4, RC4 128 bits, DESX, AES 128 bits, AES 192 bits et AES 256 bits. Les algorithmes sont implémentés à l'aide de l'API de chiffrement Windows.  
  
 Dans l'étendue d'une connexion de base de données, SQL Server peut gérer plusieurs clés symétriques ouvertes. Une clé ouverte est récupérée du magasin et est disponible pour le déchiffrement des données. Lorsqu'une donnée est déchiffrée, il est inutile de spécifier la clé symétrique à utiliser. Chaque valeur chiffrée contient l'identificateur (GUID clé) de la clé utilisée pour la chiffrer. Le moteur met en correspondance le flux d'octets chiffrés avec une clé symétrique ouverte, si la clé correcte a été déchiffrée et est ouverte. Cette clé est ensuite utilisée pour procéder au déchiffrement et retourner les données. Si la clé correcte n'est pas ouverte, la valeur NULL est retournée.  
  
 Pour obtenir un exemple qui montre comment utiliser les données chiffrées dans une base de données, consultez [chiffrer une colonne de données](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).
  
## <a name="external-resources"></a>Ressources externes  

 Pour plus d'informations sur le chiffrement des données, voir les ressources suivantes.  
  
|Ressource|Description|  
|-|-|  
|[Chiffrement SQL Server](/sql/relational-databases/security/encryption/sql-server-encryption)|Fournit une vue d'ensemble du chiffrement dans SQL Server. Cette rubrique contient des liens vers d’autres articles.|  
|[Hiérarchie de chiffrement](/sql/relational-databases/security/encryption/encryption-hierarchy)|Fournit une vue d'ensemble du chiffrement dans SQL Server. Cette rubrique fournit des liens vers d’autres articles.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Authentification dans SQL Server](authentication-in-sql-server.md)
- [Serveur et rôles de base de données dans SQL Server](server-and-database-roles-in-sql-server.md)
- [Propriété et séparation des schémas utilisateur dans SQL Server](ownership-and-user-schema-separation-in-sql-server.md)
- [Autorisation et permissions dans SQL Server](authorization-and-permissions-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
