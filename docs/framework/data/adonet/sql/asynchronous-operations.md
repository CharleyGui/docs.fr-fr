---
title: Opérations asynchrones
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: f94a33b1ff06b5433f61687b8e28096ea37b412a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197584"
---
# <a name="asynchronous-operations"></a>Opérations asynchrones

Certaines opérations de base de données, telles que les exécutions de commandes, peuvent prendre beaucoup de temps. Dans ce cas, les applications à thread unique doivent bloquer d'autres opérations et attendre que la commande soit terminée avant de poursuivre leurs propres opérations. En revanche, pouvoir affecter une opération longue à un thread d’arrière-plan permet au thread de premier plan de rester actif pendant l’opération. Dans une application Windows, par exemple, la délégation de l’opération de longue durée à un thread d’arrière-plan permet au thread d’interface utilisateur de rester réactif pendant l’exécution de l’opération.  
  
 .NET Framework comprend plusieurs modèles de design asynchrone standard que les développeurs peuvent utiliser pour tirer parti des threads d’arrière-plan et libérer l’interface utilisateur ou des threads hautement prioritaires pour l’accomplissement d’autres opérations. ADO.NET prend en charge ces mêmes modèles de design dans sa classe <xref:System.Data.SqlClient.SqlCommand>. Plus précisément, les méthodes <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>et <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>, associées aux méthodes <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A> et <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A>, fournissent le support asynchrone.  
  
> [!NOTE]
> La programmation asynchrone est une fonction clé de .NET Framework et ADO.NET exploite pleinement les modèles de design standard. Pour plus d'informations sur les différentes techniques asynchrones disponibles pour les développeurs, consultez [Appel de méthodes synchrones de façon asynchrone](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Bien que l'utilisation de techniques asynchrones avec les fonctions d'ADO.NET ne nécessite pas de commentaires particuliers, il est probable que les développeurs utiliseront les fonctions asynchrones davantage dans ADO.NET que dans d'autres domaines de .NET Framework. Il est important d'être conscient des avantages et des pièges liés à la création d'application multithread. Les exemples qui suivent dans cette section signalent plusieurs problèmes importants que les développeurs doivent prendre en compte lors de la création d’applications qui incorporent des fonctionnalités multithread.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Applications Windows utilisant des rappels](windows-applications-using-callbacks.md)  
 Fournit un exemple montrant comment exécuter une commande asynchrone en toute sécurité, en gérant correctement l’interaction avec un formulaire et son contenu à partir d’un thread distinct.  
  
 [Applications ASP.NET utilisant des handles d’attente](aspnet-apps-using-wait-handles.md)  
 Fournit un exemple montrant comment exécuter plusieurs commandes simultanées à partir d’une page ASP.NET, à l’aide de descripteurs d’attente pour gérer l’opération à l’achèvement de toutes les commandes.  
  
 [Interrogation dans les applications console](polling-in-console-applications.md)  
 Fournit un exemple illustrant l’utilisation de l’interrogation pour attendre la fin de l’exécution d’une commande asynchrone à partir d’une application console. Cette technique est également valide dans une bibliothèque de classes ou une autre application sans interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Appel de méthodes synchrones de façon asynchrone](../../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
