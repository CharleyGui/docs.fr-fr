---
title: Transactions distribuées Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a21134c3283d3d9d8d7660eecaaf74d60ecf6662
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166519"
---
# <a name="oracle-distributed-transactions"></a>Transactions distribuées Oracle

L'objet <xref:System.Data.OracleClient.OracleConnection> s'inscrit automatiquement dans une transaction distribuée existante s'il détermine qu'une transaction est active. L’inscription automatique dans une transaction se produit lorsque la connexion est ouverte et extraite du pool de connexions. Vous pouvez désactiver l'inscription automatique dans des transactions existantes en spécifiant  
  
```csharp  
Enlist=false  
```  
  
 comme paramètre de chaîne de connexion pour un <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](oracle-and-adonet.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
