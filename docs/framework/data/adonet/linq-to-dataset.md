---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 36335f90c7850fa00a15e7112b7473637250c656
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306238"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] facilite et accélère l'interrogation de données mises en cache dans un objet <xref:System.Data.DataSet>. Plus précisément, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifie l’interrogation en permettant aux développeurs d’écrire des requêtes à partir du langage de programmation lui-même, au lieu d’à l’aide d’un langage de requête séparé. Cela est particulièrement utile pour les développeurs de Visual Studio, qui peuvent désormais tirer parti de la vérification de la syntaxe de la compilation, typage statique et prise en charge de IntelliSense fournis par Visual Studio dans leurs requêtes.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] peut également être utilisé pour interroger des données qui ont été consolidées à partir d'une ou plusieurs sources de données. Cela permet plusieurs scénarios qui requièrent de la flexibilité dans la manière dont les données sont représentées et gérées, comme l'interrogation de données agrégées localement et la mise en cache en couche intermédiaire dans les applications Web. En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.  
  
 Le [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fonctionnalité est exposée principalement via les méthodes d’extension dans le <xref:System.Data.DataRowExtensions> et <xref:System.Data.DataTableExtensions> classes. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] s’appuie sur et utilise l’architecture ADO.NET existante et n’est pas censé remplacer ADO.NET dans le code d’application. Le code ADO.NET existant continuera à fonctionner dans un [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application. La relation de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] à ADO.NET et les données de magasin est illustrée dans le diagramme suivant.  
  
 ![Diagramme montrant que LINQ to DataSet est basé sur le fournisseur ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Référence  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ et ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
