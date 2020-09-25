---
title: Utilisation du langage de définition de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: c30cbbc1eae6d4cbcadb9bfe8d267fb428764971
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200886"
---
# <a name="working-with-data-definition-language"></a>Utilisation du langage de définition de données

À partir du .NET Framework version 4, le Entity Framework prend en charge le langage de définition de données (DDL). Cela vous permet de créer ou de supprimer une instance de base de données selon la chaîne de connexion et les métadonnées du modèle de stockage (SSDL).  
  
 Les méthodes suivantes sur l'objet <xref:System.Data.Objects.ObjectContext> utilisent la chaîne de connexion et le contenu SSDL pour effectuer les opérations suivantes : créer ou supprimer la base de données, vérifier si la base de données existe et consulter le script DDL généré :  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> L'exécution des commandes DDL exige de disposer d'autorisations suffisantes.  
  
 Les méthodes précédemment répertoriées délèguent la plupart du travail au fournisseur de données ADO.NET sous-jacent. Il incombe au fournisseur de vérifier que la convention d'affectation des noms utilisée pour générer les objets de base de données correspond aux conventions utilisées pour l'interrogation et les mises à jour.  
  
 L'exemple suivant vous indique comment générer la base de données selon le modèle existant. Il ajoute également un nouvel objet entité au contexte de l'objet puis l'enregistre dans la base de données.  
  
## <a name="procedures"></a>Procédures  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a>Pour définir une base de données selon le modèle existant  
  
1. Créez une application console.  
  
2. Ajoutez un modèle existant à votre application.  
  
    1. Ajoutez un modèle vide nommé `SchoolModel` . Pour créer un modèle vide, consultez la rubrique [How to : Create a New. edmx file](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) .  
  
     Le fichier SchoolModel.edmx est ajouté à votre projet.  
  
    1. Copiez le contenu conceptuel, de stockage et de mappage pour le modèle School à partir de la rubrique [modèle School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) .  
  
    2. Ouvrez le fichier SchoolModel.edmx et collez le contenu dans les balises `edmx:Runtime`.  
  
3. Ajoutez le code suivant à votre fonction principale. Le code initialise la chaîne de connexion à votre serveur de base de données, consulte le script DDL, crée la base de données, ajoute une nouvelle entité au contexte et enregistre les modifications dans la base de données.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
