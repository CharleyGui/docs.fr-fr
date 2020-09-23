---
title: LINQ to ADO.NET (page de portail)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: e1bf71a3215ef520b717336e1a30328140a5768f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083200"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (page de portail)

LINQ to ADO.NET vous permet d’interroger un objet énumérable dans ADO.NET à l’aide du modèle de programmation LINQ (Language-Integrated Query).  
  
> [!NOTE]
> La documentation LINQ to ADO.NET se trouve dans la section ADO.NET du kit de développement logiciel (SDK) .NET Framework : [LINQ et ADO.net](../../../../framework/data/adonet/linq-and-ado-net.md).
  
 Il existe trois technologies ADO.NET LINQ (Language-Integrated Query) distinctes : LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] et LINQ to Entities. LINQ to DataSet assure une interrogation plus riche et optimisée du <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] vous permet d’interroger directement des schémas de base de données SQL Server, et LINQ to Entities vous permet d’interroger un Entity Data Model.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  

 <xref:System.Data.DataSet> est l’un des composants les plus largement utilisés dans ADO.NET, et c’est un élément clé du modèle de programmation déconnecté sur lequel ADO.NET est fondé. Toutefois, en dépit de son importance, le <xref:System.Data.DataSet> a des capacités de requête limitées.  
  
 LINQ to DataSet vous permet de générer des fonctionnalités de requête plus complètes dans <xref:System.Data.DataSet> en utilisant les mêmes fonctionnalités de requête qui sont disponibles pour de nombreuses autres sources de données.  
  
 Pour plus d’informations, [consultez LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  

 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] fournit une infrastructure runtime pour la gestion des données relationnelles comme objets. Dans [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], le modèle de données d’une base de données relationnelle est mappé à un modèle objet exprimé dans le langage de programmation du développeur. Lors de l’exécution de l’application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] traduit les requêtes intégrées au langage du modèle objet en SQL et les envoie à la base de données pour exécution. Quand la base de données retourne les résultats, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] les retraduit en objets que vous pouvez utiliser.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] inclut la prise en charge des procédures stockées et fonctions définies par l’utilisateur dans la base de données, et de l’héritage dans le modèle objet.  
  
 Pour plus d’informations, consultez [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  

 Via l’Entity Data Model, les données relationnelles sont exposées comme objets dans l'environnement .NET. Cela fait de la couche objet une cible idéale pour la prise en charge de LINQ, permettant aux développeurs de formuler des requêtes sur la base de données à partir du langage utilisé pour générer la logique métier. Cette capacité est appelée LINQ to Entities. Pour plus d’informations, consultez [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Voir aussi

- [LINQ et ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [LINQ (Language-Integrated Query) (Visual Basic)](index.md)
