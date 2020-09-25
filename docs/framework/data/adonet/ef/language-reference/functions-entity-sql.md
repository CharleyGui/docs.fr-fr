---
title: Fonctions (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: bef959ae6a835b5d1d696162528a8f904c59e8e5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201068"
---
# <a name="functions-entity-sql"></a>Fonctions (Entity SQL)

Entity SQL prend en charge les fonctions définies par l'utilisateur, les fonctions canoniques et les fonctions spécifiques au fournisseur. Les fonctions définies par l'utilisateur sont spécifiées dans le modèle conceptuel ou inline dans la requête. Pour plus d’informations, consultez [fonctions définies par l’utilisateur](user-defined-functions-entity-sql.md).  
  
 Les fonctions canoniques sont prédéfinies dans Entity Framework et doivent être prises en charge par les fournisseurs de données. Les commandes Entity SQL échouent si un utilisateur appelle une fonction qui n'est pas prise en charge par un fournisseur. Par conséquent, les fonctions canoniques sont généralement recommandées par rapport aux fonctions spécifiques au magasin, qui se trouvent dans un espace de noms spécifique au fournisseur. Pour plus d’informations, consultez [fonctions canoniques](canonical-functions.md).  
  
 Le fournisseur managé Client Microsoft SQL fournit un jeu de fonctions spécifiques au fournisseur. Pour plus d’informations, consultez [SqlClient pour les fonctions de Entity Framework](../sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Fonctions définies par l'utilisateur](user-defined-functions-entity-sql.md)  
  
 [Résolution de surcharge des fonctions](function-overload-resolution-entity-sql.md)  
  
 [Fonctions d’agrégation](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
