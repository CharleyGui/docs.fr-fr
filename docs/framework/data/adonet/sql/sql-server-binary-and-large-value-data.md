---
title: Données binaires et à valeurs élevées SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791672"
---
# <a name="sql-server-binary-and-large-value-data"></a>Données binaires et à valeurs élevées SQL Server
SQL Server fournit le spécificateur `max`, qui développe la capacité de stockage des types de données `varchar`, `nvarchar` et `varbinary`. `varchar(max)`, `nvarchar(max)` et`varbinary(max)` sont collectivement appelés *types de données de valeur élevée*. Les types de données de valeur élevée permettent de stocker jusqu'à 2^31-1 octets de données.  
  
 SQL Server 2008 introduit l'attribut FILESTREAM, qui n'est pas un type de données, mais plutôt un attribut pouvant être défini sur une colonne et permettant alors de stocker des données de valeur élevée dans le système de fichiers et non dans la base de données.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modification de données de valeurs élevées (max) dans ADO.NET](modifying-large-value-max-data.md)  
 Décrit comment utiliser les types de données de valeur volumineux.  
  
 [Données FILESTREAM](filestream-data.md)  
 Décrit comment utiliser les données de valeur élevée stockées dans SQL Server 2008 avec l'attribut FILESTREAM.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [Opérations sur les données SQL Server dans ADO.NET](sql-server-data-operations.md)
- [Extraction et modification de données dans ADO.NET](../retrieving-and-modifying-data.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
