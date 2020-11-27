---
title: 'Atténuation : Période de blocage du pool'
description: Découvrez comment atténuer les problèmes provoqués par la suppression de la période de blocage du pool de connexions pour les connexions aux bases de données SQL Azure.
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 270a71790f7a602df003415e9dc6dbf784cffdd7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276566"
---
# <a name="mitigation-pool-blocking-period"></a>Atténuation : Période de blocage du pool

La période de blocage du pool de connexions a été supprimée pour les connexions aux bases de données SQL Azure.  
  
## <a name="additional-description"></a>Description complémentaire  

 Dans .NET Framework 4.6.1 et versions antérieures, quand une application rencontre un échec temporaire lors de la connexion à une base de données, la connexion ne peut pas être retentée rapidement, car le pool de connexions met l’erreur en cache, puis l’affiche de nouveau pendant 5 secondes à 1 minute. Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md). Ce comportement pose problème pour les connexions aux bases de données SQL Azure, qui échouent souvent avec des erreurs temporaires, généralement rétablies au bout de quelques secondes. La fonctionnalité de blocage du pool de connexions signifie que l’application ne peut pas se connecter à la base de données pendant une période prolongée, même si la base de données est disponible. Ce comportement est particulièrement problématique pour les applications web qui se connectent aux bases de données SQL Azure et qui doivent obtenir un affichage en quelques secondes.  
  
 À compter de .NET Framework 4.6.2, pour les demandes d’ouverture de connexion envoyées aux bases de données SQL Azure connues (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), les erreurs d’ouverture de connexion ne sont pas mises en cache. Pour toutes les autres tentatives de connexion, la période de blocage du pool de connexions continue d’être appliquée.  
  
## <a name="impact"></a>Impact  

 Ce changement permet aux demandes d’ouverture de connexion d’être retentées immédiatement pour les bases de données SQL Azure, ce qui améliore les performances des applications cloud.  
  
## <a name="mitigation"></a>Limitation des risques  

 Pour les applications qui sont affectées par ce changement, vous pouvez configurer la période de blocage du pool de connexions en définissant la nouvelle propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.  La valeur de la propriété est un membre de l’énumération <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> qui peut prendre l’une des trois valeurs suivantes :  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 Vous pouvez restaurer le comportement précédent en affectant la valeur <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
