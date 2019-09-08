---
title: Sécurité de l'intégration du CLR dans SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794560"
---
# <a name="clr-integration-security-in-sql-server"></a>Sécurité de l'intégration du CLR dans SQL Server
Microsoft SQL Server introduit le composant Common Language Runtime (CLR) du .NET Framework. L'intégration du CLR vous permet d'écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions de flux évaluées par une table, en utilisant tout langage .NET Framework, tel que Microsoft Visual Basic .NET ou Microsoft Visual C#.  
  
 Le CLR prend en charge un modèle de sécurité appelé sécurité d'accès du code (CAS) pour le code managé. Dans ce modèle, les autorisations sont accordées aux assemblys en fonction de la preuve fournie par le code dans les métadonnées. SQL Server intègre le modèle de sécurité de SQL Server, basé sur l'utilisateur avec le modèle de sécurité du CLR, basé sur l'accès du code.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations sur l'intégration du CLR avec SQL Server, voir les ressources répertoriées ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Sécurité d’accès du code](../../../misc/code-access-security.md)|Contient des rubriques qui décrivent la sécurité d'accès du code dans le .NET Framework.|  
|[Sécurité de l’intégration du CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|Présente le modèle de sécurité pour le code managé qui s'exécute au sein de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Intégration CLR SQL Server](sql-server-common-language-runtime-integration.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
