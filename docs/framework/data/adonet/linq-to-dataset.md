---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504356"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ to DataSet facilite et mis en cache plus rapide pour interroger des données dans un <xref:System.Data.DataSet> objet. En particulier, LINQ to DataSet simplifie l’interrogation en permettant aux développeurs d’écrire des requêtes à partir du langage de programmation lui-même, au lieu d’à l’aide d’un langage de requête séparé. Cela est particulièrement utile pour les développeurs de Visual Studio, qui peuvent désormais tirer parti de la vérification de la syntaxe de la compilation, typage statique et prise en charge de IntelliSense fournis par Visual Studio dans leurs requêtes.  
  
 LINQ to DataSet peut également être utilisé pour interroger des données qui ont été consolidées à partir d’une ou plusieurs sources de données. Cela permet plusieurs scénarios qui requièrent de la flexibilité dans la manière dont les données sont représentées et gérées, comme l'interrogation de données agrégées localement et la mise en cache en couche intermédiaire dans les applications Web. En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.  
  
 LINQ to DataSet fonctionnalité est exposée principalement via les méthodes d’extension dans le <xref:System.Data.DataRowExtensions> et <xref:System.Data.DataTableExtensions> classes. LINQ to DataSet s’appuie sur et utilise l’architecture ADO.NET existante et n’est pas censé remplacer ADO.NET dans le code d’application. Le code ADO.NET existant continuera à fonctionner dans une application LINQ to DataSet. La relation entre LINQ to DataSet ADO.NET et le magasin de données est illustrée dans le diagramme suivant.  
  
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
