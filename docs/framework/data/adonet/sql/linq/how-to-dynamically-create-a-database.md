---
title: 'Procédure : Créer dynamiquement une base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: e5d66b49782d5f26b6d487e655aca6fbd6bdfb1a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623867"
---
# <a name="how-to-dynamically-create-a-database"></a>Procédure : Créer dynamiquement une base de données
Dans LINQ to SQL, un modèle objet est mappé à une base de données relationnelle. Le mappage est activé à l'aide du mappage basé sur les attributs ou d'un fichier de mappage externe pour décrire la structure de la base de données relationnelle. Dans les deux scénarios, il existe suffisamment d'informations sur la base de données relationnelle pour pouvoir créer une nouvelle instance de la base de données à l'aide de la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>.  
  
 La méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> crée un réplica de la base de données uniquement en fonction de l'étendue des informations encodées dans le modèle objet. Les fichiers et les attributs de mappage de votre modèle objet ne peuvent pas encoder l'ensemble des éléments de la structure d'une base de données existante. Les informations de mappage ne représentent pas le contenu de fonctions définies par l'utilisateur, de procédures stockées, de déclencheurs ou de contraintes de validation. Ce comportement est suffisant pour différentes bases de données.  
  
 Vous pouvez utiliser la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> dans le nombre de scénarios souhaité, surtout si un fournisseur de données connu tel que Microsoft SQL Server 2008 est disponible. Dans les scénarios classiques :  
  
- Vous générez une application qui s'installe automatiquement sur le système d'un client.  
  
- Vous générez une application cliente qui a besoin d'une base de données locale pour enregistrer son état hors connexion.  
  
 Vous pouvez également utiliser la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> avec SQL Server en utilisant un fichier .mdf ou un nom de catalogue, en fonction de votre chaîne de connexion. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise la chaîne de connexion pour définir la base de données à créer et sur quel serveur la base de données sera créée.  
  
> [!NOTE]
>  Si possible, utilisez la sécurité intégrée Windows pour vous connecter à la base de données de façon à ce que les mots de passe ne soient pas requis dans la chaîne de connexion.  
  
## <a name="example"></a>Exemple  
 Le code suivant fournit un exemple de création d'une nouvelle base de données nommée MyDVDs.mdf.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser le modèle objet pour créer une base de données en procédant comme suit :  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Exemple  
 Lors de la création d’une application qui s’installe automatiquement sur le système d’un client, vérifiez si la base de données existe déjà et supprimez-la avant d’un créer une nouvelle. La classe <xref:System.Data.Linq.DataContext> fournit les méthodes <xref:System.Data.Linq.DataContext.DatabaseExists%2A> et <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> pour vous aider dans cette tâche.  
  
 L'exemple suivant illustre une utilisation de ces méthodes pour implémenter cette approche :  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Voir aussi

- [Mappage basé sur les attributs](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Mappage de type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
