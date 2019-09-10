---
title: Écriture d'un fournisseur de données Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854164"
---
# <a name="writing-an-entity-framework-data-provider"></a>Écriture d'un fournisseur de données Entity Framework
Cette section explique comment écrire un fournisseur Entity Framework pour prendre en charge une source de données autre que SQL Server. Le Entity Framework comprend un fournisseur qui prend en charge les SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Présentation du modèle de fournisseur Entity Framework  
 La Entity Framework est indépendante de la base de données, et vous pouvez écrire un fournisseur à l’aide du modèle de fournisseur ADO.NET pour vous connecter à un ensemble diversifié de sources de données.  
  
 Le fournisseur de données Entity Framework (construit à l’aide du modèle de fournisseur de données ADO.NET) effectue les fonctions suivantes :  
  
- Mappe des types primitifs d'Entity Data Model (EDM) aux types de fournisseurs.  
  
- Expose des fonctions spécifiques au fournisseur.  
  
- Génère des commandes spécifiques au fournisseur pour un DbQueryCommandTree donné afin de prendre en charge les requêtes Entity Framework.  
  
- Génère des commandes de mise à jour spécifiques au fournisseur pour un DbModificationCommandTree donné afin de prendre en charge les mises à jour via l’Entity Framework.  
  
- Expose des fichiers de mappage pour la définition de schéma du magasin afin de prendre en charge la génération d'un modèle selon une base de données.  
  
- Expose des métadonnées (tables et vues, par exemple) via un modèle conceptuel.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Exemple  
 Consultez l' [exemple de fournisseur de Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) pour obtenir un exemple de fournisseur d’Entity Framework qui prend en charge une source de données autre que SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Génération SQL](sql-generation.md)  
  
 [Génération SQL de modification](modification-sql-generation.md)  
  
 [Spécification de manifeste du fournisseur](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des fournisseurs de données](working-with-data-providers.md)
