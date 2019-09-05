---
title: Remarques sur le déploiement (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 3e78fc413e50deda67aa8992179e500afa671f8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251617"
---
# <a name="deployment-considerations-entity-framework"></a>Remarques sur le déploiement (Entity Framework)
Cette rubrique fournit des informations sur le déploiement d’applications qui utilisent ADO.NET Entity Framework pour l’accès aux données. Pour plus d’informations sur la Entity Framework, consultez [prise en main](getting-started.md).  
  
 Entity Framework propose un ensemble d’outils qui s’intègrent à Visual Studio et facilitent le développement dans cet environnement. Pour plus d’informations, consultez [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)). Cette rubrique ne décrit pas comment utiliser des technologies spécifiques pour déployer une application Entity Framework.  
  
 Visual Studio propose des fonctions de distribution et de déploiement d'applications, comme le déploiement ClickOnce. Pour plus d’informations, consultez [déploiement d’applications et de composants](/visualstudio/deployment/deploying-applications-services-and-components) dans la documentation de Visual Studio.  
  
 Vous devez tenir compte des points suivants lorsque vous déployez une application qui utilise Entity Framework :  
  
- Entity Framework est un composant du .NET Framework depuis la version .NET Framework 3.5 Service Pack 1 (SP1). Vous devez vous assurer que .NET Framework SP1 ou une version ultérieure est installée lors du déploiement d'une application Entity Framework.  
  
- Lorsqu'un modèle conceptuel est généré par l'Assistant EDM, une chaîne de connexion est créée dans le fichier de configuration de l'application. Les fichiers de mappage et de modèle peuvent être incorporés comme ressources d'application ou ils peuvent être copiés dans le répertoire de sortie. Par défaut, ils sont déployés en tant que ressources d'application incorporées. Utilisez la propriété `Metadata Artifact Processing` du fichier du concepteur d'entités pour sélectionner l'une de ces options. Pour plus d’informations, consultez [Guide pratique pour Copiez les fichiers de modèle et de mappage](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100))dans le répertoire de sortie.  
  
- Vérifiez que les informations de mappage et de modèle (exprimées dans les langages CSDL (Conceptual Schema Definition Language), SSDL (Store Schema Definition Language) et MSL (Mapping Specification Language)) sont déployées avec l'application et dans l'emplacement spécifié par la chaîne de connexion. Pour plus d’informations, consultez [Chaînes de connexion](connection-strings.md).  
  
- Lorsque vous incorporez des informations de mappage et de modèle en tant que ressources d'application, vous devez recompiler et redéployer l'application chaque fois que le modèle conceptuel est mis à jour.  
  
- Entity Framework étant un composant du .NET Framework, il peut ainsi être redistribué avec votre application si le contrat de licence du .NET Framework l’autorise.  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](index.md)
- [Points à prendre en considération pour le développement et le déploiement](development-and-deployment-considerations.md)
