---
title: Création d'un DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203895"
---
# <a name="creating-a-datareader"></a>Création d'un DataReader
Les classes <xref:System.Data.DataTable> et <xref:System.Data.DataSet> ont une méthode <xref:System.Data.DataTable.CreateDataReader%2A> qui retourne le contenu de la collection <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> ou de l'objet <xref:System.Data.DataSet.Tables%2A> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.  
  
## <a name="example"></a>Exemples  
 L'application console suivante crée une instance de l'objet <xref:System.Data.DataTable>. L’exemple passe ensuite le rempli <xref:System.Data.DataTable> à une procédure qui appelle la <xref:System.Data.DataTable.CreateDataReader%2A> méthode, qui itère au sein des résultats contenus dans le <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 L'exemple affiche la sortie suivante dans la fenêtre de console :  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [DataTableReaders](datatablereaders.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
