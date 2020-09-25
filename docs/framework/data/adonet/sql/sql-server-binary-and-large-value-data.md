---
title: Données binaires et à valeurs élevées SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: a9296e83b0f4e4352423470433670bb2cbe5a248
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183037"
---
# <a name="sql-server-binary-and-large-value-data"></a>Données binaires et à valeurs élevées SQL Server

SQL Server fournit le spécificateur `max`, qui étend la capacité de stockage des types de données `varchar`, `nvarchar` et `varbinary`. `varchar(max)`, `nvarchar(max)` et `varbinary(max)` sont collectivement appelés *types de données de valeur élevée*. Les types de données de valeur élevée permettent de stocker jusqu’à 2^31-1 octets de données.  
  
 SQL Server 2008 introduit l’attribut FILESTREAM, qui n’est pas un type de données, mais plutôt un attribut qui peut être défini sur une colonne, et permet de stocker des données de grande valeur sur le système de fichiers plutôt que dans la base de données.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Modification de données de valeur élevée (max) dans ADO.NET](modifying-large-value-max-data.md)  
 Décrit comment utiliser les types de données de valeur volumineux.  
  
 [Données FILESTREAM](filestream-data.md)  
 Décrit comment utiliser les données de valeur élevée stockées dans SQL Server 2008 avec l’attribut FILESTREAM.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [SQL Server des opérations de données dans ADO.NET](sql-server-data-operations.md)
- [Extraction et modification de données dans ADO.NET](../retrieving-and-modifying-data.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
