---
title: Transactions distribuées Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 6f910f1dbbe448352c0edd5d1b80df659ac453d4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795150"
---
# <a name="oracle-distributed-transactions"></a>Transactions distribuées Oracle
L'objet <xref:System.Data.OracleClient.OracleConnection> s'inscrit automatiquement dans une transaction distribuée existante s'il détermine qu'une transaction est active. L’inscription automatique dans une transaction se produit lorsque la connexion est ouverte et extraite du pool de connexions. Vous pouvez désactiver l'inscription automatique dans des transactions existantes en spécifiant  
  
```  
Enlist=false  
```  
  
 comme paramètre de chaîne de connexion pour un <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](oracle-and-adonet.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
