---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 1c03cca80de6003a4e49278871983ed7fcb3dc0b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200665"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet

LINQ to DataSet facilite et accélère l’interrogation de données mises en cache dans un <xref:System.Data.DataSet> objet. Plus précisément, LINQ to DataSet simplifie l’interrogation en permettant aux développeurs d’écrire des requêtes à partir du langage de programmation lui-même, au lieu d’utiliser un langage de requête séparé. Ceci est particulièrement utile pour les développeurs Visual Studio, qui peuvent désormais tirer parti de la vérification de la syntaxe au moment de la compilation, du typage statique et de la prise en charge IntelliSense fournis par Visual Studio dans leurs requêtes.  
  
 LINQ to DataSet peut également être utilisé pour interroger des données qui ont été consolidées à partir d’une ou de plusieurs sources de données. Cela permet plusieurs scénarios qui requièrent de la flexibilité dans la manière dont les données sont représentées et gérées, comme l'interrogation de données agrégées localement et la mise en cache en couche intermédiaire dans les applications Web. En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.  
  
 La fonctionnalité de LINQ to DataSet est exposée principalement à travers les méthodes d’extension dans les <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> classes et. LINQ to DataSet repose sur et utilise l’architecture ADO.NET existante et n’est pas destinée à remplacer ADO.NET dans le code de l’application. Le code ADO.NET existant continuera à fonctionner dans une application LINQ to DataSet. La relation entre LINQ to DataSet et ADO.NET et le magasin de données est illustrée dans le diagramme suivant.  
  
 ![Diagramme montrant que LINQ to DataSet est basé sur le fournisseur ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>Dans cette section  

 [Prise en main](getting-started-linq-to-dataset.md)  
  
 [Guide de programmation](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ et ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)
