---
title: Prise en charge de SqlClient pour la haute disponibilité et la récupération d'urgence
ms.date: 03/30/2017
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.openlocfilehash: aa4c716dc1b27d50620777613e698ca6dbab31d8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487633"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>Prise en charge de SqlClient pour la haute disponibilité et la récupération d'urgence
Cette rubrique décrit la prise en charge de SqlClient (ajoutée dans .NET Framework 4.5) haute disponibilité et récupération d’urgence--groupes de disponibilité AlwaysOn.  Fonctionnalité de groupes de disponibilité AlwaysOn a été ajoutée à SQL Server 2012. Pour plus d’informations sur les groupes de disponibilité AlwaysOn, consultez la documentation en ligne de SQL Server.  
  
 Vous pouvez désormais spécifier l’écouteur de groupe de disponibilité d’une (haute disponibilité et récupération d’urgence) groupe de disponibilité (AG) ou l’Instance de Cluster de basculement SQL Server 2012 dans la propriété de connexion. Si une application SqlClient est connectée à une base de données AlwaysOn qui bascule, la connexion initiale est interrompue et l'application doit ouvrir une nouvelle connexion pour continuer les tâches après le basculement.  
  
 Si vous n’êtes pas connecté à un écouteur de groupe de disponibilité ou d’une Instance de Cluster de basculement SQL Server 2012, et si plusieurs adresses IP sont associées à un nom d’hôte, SqlClient sera itérer séquentiellement toutes les adresses IP associées avec l’entrée DNS. Cela peut prendre du temps si la première adresse IP retournée par le serveur DNS n'est liée à aucune carte d'interface réseau. Lors de la connexion à un écouteur de groupe de disponibilité ou d’une Instance de Cluster de basculement SQL Server 2012, SqlClient tente d’établir des connexions à toutes les adresses IP en parallèle et si une tentative de connexion réussit, le pilote ignore toute connexion en attente tentatives.  
  
> [!NOTE]
>  L'augmentation du délai de connexion et l'implémentation de la logique de nouvelles tentatives de connexion augmentent la probabilité qu'une application se connecte à un groupe de disponibilité. En outre, étant donné qu'une connexion peut échouer en raison d'un basculement, vous devez implémenter la logique pour les nouvelles tentatives de connexion, nouvelle tentative de connexion jusqu'à reconnexion.  
  
 Les propriétés de connexion suivantes ont été ajoutées à SqlClient dans .NET Framework 4.5 :  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
 Vous pouvez modifier par programmation ces mots clés de chaîne de connexion avec :  
  
1. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
2. <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  

> [!NOTE]
>  Paramètre `MultiSubnetFailover` à `true` n’est pas nécessaire avec .NET Framework 4.6.1 ou version ultérieure.
  
## <a name="connecting-with-multisubnetfailover"></a>Connexion avec MultiSubnetFailover  
 Spécifiez toujours `MultiSubnetFailover=True` lors de la connexion à un écouteur de groupe de disponibilité de SQL Server 2012 ou une Instance de Cluster de basculement SQL Server 2012. `MultiSubnetFailover` permet un basculement plus rapide pour tous les groupes de disponibilité et ou Instance de Cluster de basculement dans SQL Server 2012 et réduire considérablement le temps de basculement pour les topologies AlwaysOn de sous-réseaux uniques et multiples. Pendant un basculement de multi sous-réseau, le client effectue des tentatives de connexion en parallèle. Pendant un basculement de sous-réseau, le client effectue des tentatives de connexion TCP de manière agressive.  
  
 Le `MultiSubnetFailover` propriété de connexion indique que l’application est déployée dans un groupe de disponibilité ou d’une Instance de Cluster de basculement SQL Server 2012 et que SqlClient tente de se connecter à la base de données sur l’instance de SQL Server principale en essayant de se connecter à toutes les adresses IP. Lorsque `MultiSubnetFailover=True` est spécifié pour une connexion, le client effectue des tentatives de connexion TCP plus rapidement que les intervalles de retransmission TCP par défaut du système d'exploitation. Cela permet une reconnexion plus rapide après basculement d'un groupe de disponibilité AlwaysOn ou d'une instance de cluster de basculement AlwaysOn, et s'applique aux groupes de disponibilité de sous-réseau unique et de multi-sous-réseau et aux instances de cluster de basculement.  
  
 Pour plus d'informations sur les mots clés de chaîne de connexion dans SqlClient, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Spécification `MultiSubnetFailover=True` lorsque la connexion à un élément autre qu’un écouteur du groupe de disponibilité ou d’une Instance de Cluster de basculement SQL Server 2012 peut entraîner un impact sur les performances et n’est pas pris en charge.  
  
 Utilisez les instructions suivantes pour vous connecter à un serveur dans un groupe de disponibilité ou Instance de Cluster de basculement SQL Server 2012 :  
  
- Utilisez la propriété de connexion `MultiSubnetFailover` lors de la connexion à un sous-réseau unique ou à un multi-sous-réseau ; elle permet d'améliorer les performances pour les deux.  
  
- Pour vous connecter à un groupe de disponibilité, spécifiez l'écouteur du groupe de disponibilité en tant que serveur dans votre chaîne de connexion.  
  
- Connexion à un serveur SQL Server instance configurée avec plus de 64 adresses IP entraînera un échec de connexion.  
  
- Comportement d’une application qui utilise le `MultiSubnetFailover` propriété de connexion n’est pas affectée selon le type d’authentification : L’authentification SQL Server, l’authentification Kerberos ou l’authentification Windows.  
  
- Augmentez la valeur de `Connect Timeout` pour permettre la prise en charge pour le temps de basculement et réduire les tentatives de nouvelle connexion d'application.  
  
- Les transactions distribuées ne sont pas prises en charge.  
  
 Si le routage en lecture seule n'est pas appliqué, la connexion à un emplacement de réplica secondaire échoue dans les situations suivantes :  
  
1. Si l'emplacement de réplica secondaire n'est pas configuré pour recevoir des connexions.  
  
2. Si une application utilise `ApplicationIntent=ReadWrite` (voir ci-dessous) et l'emplacement de réplica secondaire est configuré pour l'accès en lecture seule.  
  
 <xref:System.Data.SqlClient.SqlDependency> n'est pas pris en charge sur des réplicas secondaires en lecture seule.  
  
 Une connexion échoue si un réplica principal est configuré pour rejeter les charges de travail en lecture seule et la chaîne de connexion contient `ApplicationIntent=ReadOnly`.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Mise à niveau pour utiliser des clusters de multi-sous-réseaux de mise en miroir de bases de données  
 Une erreur de connexion (<xref:System.ArgumentException>) se produira si les mots clés de connexion `MultiSubnetFailover` et `Failover Partner` sont présents dans la chaîne de connexion, ou si `MultiSubnetFailover=True` et un protocole autre que TCP est utilisé. Une erreur (<xref:System.Data.SqlClient.SqlException>) se produit également si `MultiSubnetFailover` est utilisé et le serveur SQL Server retourne une réponse de partenaire de basculement indiquant qu’il fait partie d’une paire de mise en miroir de base de données.  
  
 Si vous mettez à niveau une application SqlClient qui utilise actuellement la mise en miroir de bases de données dans un scénario de multi-sous-réseau, vous devez supprimer la propriété de connexion `Failover Partner` et la remplacer par `MultiSubnetFailover` ayant la valeur `True` et remplacer le nom du serveur dans la chaîne de connexion par un écouteur du groupe de disponibilité. Si une chaîne de connexion utilise `Failover Partner` et `MultiSubnetFailover=True`, le pilote génère une erreur. Toutefois, si une chaîne de connexion utilise `Failover Partner` et `MultiSubnetFailover=False` (ou `ApplicationIntent=ReadWrite`), l'application utilise la mise en miroir de bases de données.  
  
 Le pilote retourne une erreur si la mise en miroir de bases de données est utilisée dans la base de données principale du groupe de disponibilité, et si `MultiSubnetFailover=True` est utilisé dans la chaîne de connexion qui se connecte à une base de données principale plutôt qu'à un écouteur du groupe de disponibilité.  
  
## <a name="specifying-application-intent"></a>Spécification de l'intention d'application  
 Lorsque `ApplicationIntent=ReadOnly`, le client demande une charge de travail de lecture lors de la connexion à une base de données AlwaysOn. Le serveur applique l'intention au moment de la connexion et pendant une instruction de base de données USE, mais uniquement à une base de données AlwaysOn.  
  
 Le mot clé `ApplicationIntent` ne fonctionne pas avec les bases de données en lecture seule héritées.  
  
 Une base de données peut autoriser ou interdire les charges de travail de lecture sur la base de données ciblée AlwaysOn. (Cette opération est effectuée avec la `ALLOW_CONNECTIONS` clause de le `PRIMARY_ROLE` et `SECONDARY_ROLE`instructions Transact-SQL.)  
  
 Le mot clé `ApplicationIntent` est utilisé pour permettre le routage en lecture seule.  
  
## <a name="read-only-routing"></a>Routage en lecture seule  
 Le routage en lecture seule est une fonctionnalité qui garantit la disponibilité d'un réplica en lecture seule d'une base de données. Pour activer le routage en lecture seule :  
  
1. Vous devez vous connecter à un écouteur du groupe de disponibilité Groupe de disponibilité AlwaysOn.  
  
2. Le mot clé de chaîne de connexion `ApplicationIntent` doit avoir la valeur `ReadOnly`.  
  
3. Le groupe de disponibilité doit être configuré par l'administrateur de base de données pour permettre le routage en lecture seule.  
  
 Il est possible que plusieurs connexions utilisant le routage en lecture seule ne se connectent pas au même réplica en lecture seule. Les modifications de la synchronisation de base de données ou les modifications de la configuration du routage du serveur peuvent entraîner des connexions clientes à des réplicas en lecture seule. Pour vous assurer que toutes les demandes en lecture seule se connectent au même réplica en lecture seule, ne passez pas un écouteur du groupe de disponibilité au mot clé de chaîne de connexion `Data Source`. À la place, spécifiez le nom de l'instance en lecture seule.  
  
 Le routage en lecture seule peut prendre plus longtemps que la connexion au principal, car il se connecte d'abord au principal, puis recherche le meilleur réplica secondaire lisible disponible. De ce fait, vous devez augmenter le délai d'attente de connexion.  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnalités SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
