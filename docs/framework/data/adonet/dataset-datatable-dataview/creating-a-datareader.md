---
title: Création d'un DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 79cb2ce7ffae81aeba9aaca557e37ba566a8370c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784765"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="49d75-102">Création d'un DataReader</span><span class="sxs-lookup"><span data-stu-id="49d75-102">Creating a DataReader</span></span>
<span data-ttu-id="49d75-103">Les classes <xref:System.Data.DataTable> et <xref:System.Data.DataSet> ont une méthode <xref:System.Data.DataTable.CreateDataReader%2A> qui retourne le contenu de la collection <xref:System.Data.DataTable> de l'objet <xref:System.Data.DataSet> ou de l'objet <xref:System.Data.DataSet.Tables%2A> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="49d75-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49d75-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="49d75-104">Example</span></span>  
 <span data-ttu-id="49d75-105">L'application console suivante crée une instance de l'objet <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="49d75-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="49d75-106">L’exemple passe ensuite le rempli <xref:System.Data.DataTable> à une procédure qui appelle la <xref:System.Data.DataTable.CreateDataReader%2A> méthode, qui itère au sein des résultats contenus dans le <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="49d75-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="49d75-107">L'exemple affiche la sortie suivante dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="49d75-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="49d75-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49d75-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="49d75-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="49d75-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="49d75-110">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49d75-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
