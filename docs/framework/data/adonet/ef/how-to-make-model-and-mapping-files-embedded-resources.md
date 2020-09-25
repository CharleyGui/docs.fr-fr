---
title: 'Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 8496dcad5422d1a45af52e58325efd360768da34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198286"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Procédure : Transformer les fichiers modèle et les fichiers de mappage en ressources incorporées

Le Entity Framework vous permet de déployer des fichiers de modèle et de mappage en tant que ressources incorporées d’une application. L'assembly comprenant les fichiers de mappage et de modèle incorporés doit être chargé dans le même domaine d'application que la connexion d'entité. Pour plus d’informations, consultez [chaînes de connexion](connection-strings.md). Par défaut, les outils de Entity Data Model incorporent les fichiers de modèle et de mappage. Lorsque vous définissez manuellement les fichiers de modèle et de mappage, utilisez cette procédure pour vous assurer que les fichiers sont déployés en tant que ressources incorporées avec une application Entity Framework.  
  
> [!NOTE]
> Pour conserver des ressources incorporées, vous devez répéter cette procédure chaque fois que les fichiers de mappage et de modèle sont modifiés.  
  
### <a name="to-embed-model-and-mapping-files"></a>Pour incorporer les fichiers de mappage et de modèle  
  
1. Dans **Explorateur de solutions**, sélectionnez le fichier conceptuel (. CSDL).  
  
2. Dans le volet **Propriétés** , affectez à **action de génération** la valeur **ressource incorporée**.  
  
3. Répétez les étapes 1 et 2 pour le fichier de stockage (.ssdl) et le fichier de mappage (.msl).  
  
4. Dans **Explorateur de solutions**, double-cliquez sur le fichier App.config, puis modifiez le `Metadata` paramètre dans l' `connectionString` attribut en fonction de l’un des formats suivants :  
  
    - `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=` `res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     Pour plus d’informations, consultez [chaînes de connexion](connection-strings.md).  
  
## <a name="example"></a>Exemple  

 La chaîne de connexion suivante référence les fichiers de mappage et de modèle incorporés pour le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Cette chaîne de connexion est stockée dans le fichier App.config du projet.  

## <a name="see-also"></a>Voir aussi

- [Modélisation et mappage](modeling-and-mapping.md)
- [Procédure : Définir la chaîne de connexion](how-to-define-the-connection-string.md)
- [Procédure : Créer une chaîne de connexion EntityConnection](how-to-build-an-entityconnection-connection-string.md)
- [Outils de Entity Data Model ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
