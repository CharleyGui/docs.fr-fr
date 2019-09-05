---
title: Écriture d'un fournisseur de données Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248186"
---
# <a name="writing-an-entity-framework-data-provider"></a>Écriture d'un fournisseur de données Entity Framework
Cette section explique comment écrire un [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fournisseur pour prendre en charge une source de données autre que SQL Server. Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] comprend un fournisseur qui prend en charge SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Présentation du modèle de fournisseur Entity Framework  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] est une base de données indépendante et il est possible d'écrire un fournisseur à l'aide du modèle de fournisseur ADO.NET pour se connecter à un jeu divers de sources de données.  
  
 Le fournisseur de données Entity Framework (construit à l’aide du modèle de fournisseur de données ADO.NET) effectue les fonctions suivantes :  
  
- Mappe des types primitifs d'Entity Data Model (EDM) aux types de fournisseurs.  
  
- Expose des fonctions spécifiques au fournisseur.  
  
- Génère des commandes spécifiques au fournisseur pour un DbQueryCommandTree donné afin de prendre en charge des requêtes [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
- Génère des commandes de mise à jour spécifiques au fournisseur pour un DbModificationCommandTree donné pour prendre en charge les mises à jour via [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
- Expose des fichiers de mappage pour la définition de schéma du magasin afin de prendre en charge la génération d'un modèle selon une base de données.  
  
- Expose des métadonnées (tables et vues, par exemple) via un modèle conceptuel.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Exemple  
 Consultez l' [exemple de fournisseur de Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) pour obtenir un [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] exemple de fournisseur qui prend en charge une source de données autre que SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Génération SQL](sql-generation.md)  
  
 [Génération SQL de modification](modification-sql-generation.md)  
  
 [Spécification de manifeste du fournisseur](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des fournisseurs de données](working-with-data-providers.md)
