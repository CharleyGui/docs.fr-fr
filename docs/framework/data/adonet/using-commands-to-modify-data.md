---
title: Utilisation des commandes pour modifier les données
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: e2f61dbf74f28d026ae91a2bc8f5bb78530ffeac
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177252"
---
# <a name="using-commands-to-modify-data"></a>Utilisation des commandes pour modifier les données

À l'aide d'un fournisseur de données .NET Framework, vous pouvez exécuter des procédures stockées ou des instructions DDL (CREATE TABLE et ALTER COLUMN, par exemple) pour effectuer une manipulation de schéma sur une base de données ou un catalogue. Ces commandes ne retournent pas de lignes en tant que requête, donc l’objet **Command** fournit un **ExecuteNonQuery** pour les traiter.  
  
 Outre l’utilisation de **ExecuteNonQuery** pour modifier le schéma, vous pouvez également utiliser cette méthode pour traiter les instructions SQL qui modifient les données, mais qui ne retournent pas de lignes, telles que Insert, Update et DELETE.  
  
 Bien que les lignes ne soient pas retournées par la méthode **ExecuteNonQuery** , les paramètres d’entrée et de sortie et les valeurs de retour peuvent être passés et retournés via la collection **Parameters** de l’objet **Command** .  
  
## <a name="in-this-section"></a>Dans cette section  

 [Mise à jour des données dans une source de données](updating-data-in-a-data-source.md)  
 Décrit l'exécution de commandes ou de procédures stockées qui modifient les données dans une base de données.  
  
 [Exécution d'opérations du catalogue](performing-catalog-operations.md)  
 Décrit l'exécution des commandes qui modifient le schéma de base de données.  
  
## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
