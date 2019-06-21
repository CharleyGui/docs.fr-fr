---
title: 'Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 3abb0ead210903a4ac2d16e4a977aaefbcde8ceb
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307356"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées
Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vous permet de déployer des fichiers de mappage et de modèle en tant que ressources incorporées d’une application. L'assembly comprenant les fichiers de mappage et de modèle incorporés doit être chargé dans le même domaine d'application que la connexion d'entité. Pour plus d’informations, consultez [Chaînes de connexion](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Par défaut, les outils Entity Data Model incorporent les fichiers de mappage et de modèle. Lorsque vous définissez manuellement les fichiers de mappage et de modèle, utilisez cette procédure pour garantir que les fichiers sont déployés en tant que ressources incorporées avec une application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Pour conserver des ressources incorporées, vous devez répéter cette procédure chaque fois que les fichiers de mappage et de modèle sont modifiés.  
  
### <a name="to-embed-model-and-mapping-files"></a>Pour incorporer les fichiers de mappage et de modèle  
  
1. Dans **l’Explorateur de solutions**, sélectionnez le fichier conceptuel (.csdl).  
  
2. Dans le **propriétés** volet, définissez **Action de génération** à **ressource incorporée**.  
  
3. Répétez les étapes 1 et 2 pour le fichier de stockage (.ssdl) et le fichier de mappage (.msl).  
  
4. Dans **l’Explorateur de solutions**, double-cliquez sur le fichier App.config et ensuite modifier le `Metadata` paramètre dans le `connectionString` attribut basé sur l’un des formats suivants :  
  
    - `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=` `res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     Pour plus d’informations, consultez [Chaînes de connexion](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Exemple  
 Fait référence à la chaîne de connexion pour les fichiers de mappage et de modèle incorporés le [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Cette chaîne de connexion est stockée dans le fichier App.config du projet.  

## <a name="see-also"></a>Voir aussi

- [Modélisation et mappage](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [Guide pratique pour Définir la chaîne de connexion](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)
- [Guide pratique pour Créer une chaîne de connexion EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)
- [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
