---
title: LINQ to ADO.NET (page de portail)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 84412e43a9d6b1e256e4ac8306a94126a3eaaaf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635546"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (page de portail)
LINQ pour ADO.NET vous permet d’interroger sur n’importe quel objet enumérable dans ADO.NET en utilisant le modèle de programmation de la requête intégrée en langue (LINQ).  
  
> [!NOTE]
> La DOCUMENTATION LINQ pour ADO.NET est située dans la section ADO.NET du cadre .NET SDK : [LINQ et ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Il existe trois technologies distinctes ADO.NET de requêtes intégrées en langue (LINQ) : LINQ à DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]et LINQ aux entités. LINQ to DataSet assure une interrogation plus riche et optimisée du <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] vous permet d’interroger directement des schémas de base de données SQL Server, et LINQ to Entities vous permet d’interroger un Entity Data Model.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> est l’un des composants les plus largement utilisés dans ADO.NET, et c’est un élément clé du modèle de programmation déconnecté sur lequel ADO.NET est fondé. Toutefois, en dépit de son importance, le <xref:System.Data.DataSet> a des capacités de requête limitées.  
  
 LINQ to DataSet vous permet de générer des fonctionnalités de requête plus complètes dans <xref:System.Data.DataSet> en utilisant les mêmes fonctionnalités de requête qui sont disponibles pour de nombreuses autres sources de données.  
  
 Pour plus d’informations, [consultez LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] fournit une infrastructure runtime pour la gestion des données relationnelles comme objets. Dans [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], le modèle de données d’une base de données relationnelle est mappé à un modèle objet exprimé dans le langage de programmation du développeur. Lors de l’exécution de l’application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] traduit les requêtes intégrées au langage du modèle objet en SQL et les envoie à la base de données pour exécution. Quand la base de données retourne les résultats, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] les retraduit en objets que vous pouvez utiliser.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] inclut la prise en charge des procédures stockées et fonctions définies par l’utilisateur dans la base de données, et de l’héritage dans le modèle objet.  
  
 Pour plus d’informations, consultez [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Via l’Entity Data Model, les données relationnelles sont exposées comme objets dans l'environnement .NET. Cela fait de la couche d’objet une cible idéale pour le support LINQ, permettant aux développeurs de formuler des requêtes contre la base de données à partir du langage utilisé pour construire la logique d’entreprise. Cette capacité est appelée LINQ to Entities. Pour plus d’informations, consultez [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Voir aussi

- [LINQ et ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [LINQ (Language-Integrated Query) (C#)](./index.md)
