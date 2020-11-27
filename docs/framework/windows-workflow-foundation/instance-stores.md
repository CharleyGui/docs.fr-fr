---
title: Magasins d'instances
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 0e3cc0c6c635d9c42b4242581ce039b186116113
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279868"
---
# <a name="instance-stores"></a>Magasins d'instances

Un magasin d'instances est un conteneur logique d'instances. Il s'agit de l'endroit où les données et les métadonnées d'instance sont stockées. Un magasin d'instances n'implique pas de stockage physique dédié. Il peut contenir des informations durables dans une base de données SQL Server ou des informations d'état non durables dans une mémoire. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] est fourni avec le magasin d'instances de workflow SQL, lequel est une implémentation concrète d'un magasin d'instances qui permet aux workflows de rendre des données et des métadonnées d'instance persistantes dans une base de données SQL Server 2005 ou 2008. En outre, Windows Server AppFabric fournit également une implémentation concrète d'un magasin d'instances. Pour plus d’informations, consultez [magasin d’instances, requêtes et fournisseurs de contrôles Windows Server App Fabric](/previous-versions/appfabric/ff383417(v=azure.10)).  
  
 L'API de persistance est l'interface entre un hôte et un magasin d'instances qui permet à l'hôte d'envoyer des demandes de commande (par exemple, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> et <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) au magasin d'instances. L'implémentation concrète de cette API est appelée fournisseur de persistance. Le fournisseur de persistance reçoit des demandes d'un hôte et modifie le magasin d'instances.  
  
 Les hôtes et les magasins d'instances sont enfichables afin qu'un hôte puisse être utilisé avec de nombreux magasins d'instances et qu'un magasin d'instances puisse être utilisé avec de nombreux hôtes. Un magasin d’instances est généralement optimisé pour les modèles d’utilisation d’un hôte particulier, bien que le magasin d’instances et l’hôte puissent évoluer sur des cycles de vie indépendants. Par exemple, les **WorkflowServiceHost** et les **SqlWorkflowInstanceStore** sont conçus pour fonctionner correctement ensemble. Vous pouvez créer votre propre magasin d’instances pour conserver les données et les métadonnées des instances de service de workflow et utiliser ce magasin d’instances avec **WorkflowServiceHost**. Par exemple, vous pouvez créer un OracleWorkflowInstanceStore qui laisse des workflows rendre les informations persistantes dans une base de données Oracle au lieu de les enregistrer dans une base de données SQL Server.  
  
 Il est courant que les hôtes soient étendus avec des fonctionnalités supplémentaires qui modifient les objets rendus persistants. Par exemple, un système de persistance d’instance peut avoir un hôte de workflow, une extension qui prend en charge l’opération d’interruption et un magasin d’instances SQL.  L'hôte de workflow peut envoyer une commande standard telle que Save ou Load pour enregistrer ou charger un workflow à partir d'un magasin d'instances ou pour enregistrer un workflow dans un magasin d'instances. L'extension d'interruption peut ajouter une sémantique supplémentaire aux commandes pour enregistrer et charger des instances de workflow afin qu'une instance de workflow interrompue ne puisse pas être chargée. Le fournisseur de persistance du magasin d'instances SQL comprend les commandes d'enregistrement et de chargement des instances de workflow et implémente ces commandes en appelant des procédures stockées appropriées qui modifient les tables d'objets persistants dans une base de données SQL Server.  
  
 Un hôte agit comme un propriétaire d'instance dans un magasin d'instances. Il peut se comporter comme le propriétaire de plusieurs instances avec plusieurs magasins d'instances en même temps. L'hôte fournit des GUID pour les clés d'instance associées aux instances. Une clé d'instance est un alias unique qui identifie une instance. Le système de persistance crée, met à jour et supprime les informations de propriétaire d'instance à mesure qu'il exécute les commandes demandées par les hôtes.  
  
 La liste suivante répertorie les étapes importantes de l'interaction de l'hôte avec le magasin d'instances :  
  
1. Obtenez un **InstanceStore** à partir d’un fournisseur de persistance.  

2. Obtenez le handle d’une instance en appelant la <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> méthode sur le **InstanceStore**.  
  
3. Appelez les commandes sur le handle d’instance en appelant la <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> méthode sur **InstanceStore**.  
  
4. Examinez la <xref:System.Runtime.DurableInstancing.InstanceView> valeur retournée par **InstanceStore.Exe** pour déterminer les résultats des commandes.
