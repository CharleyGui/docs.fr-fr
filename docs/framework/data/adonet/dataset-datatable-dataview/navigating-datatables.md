---
title: Navigation sur les DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: b5837d647b72f8dd17c4a6d3664faf8976243d36
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204560"
---
# <a name="navigating-datatables"></a>Navigation sur les DataTable
L'objet <xref:System.Data.DataTableReader> obtient le contenu d'un ou plusieurs objets <xref:System.Data.DataTable> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.  
  
 Un objet <xref:System.Data.DataTableReader> peut contenir plusieurs jeux de résultats s'il est créé à l'aide de la méthode <xref:System.Data.DataSet.CreateDataReader%2A>. S'il y a plusieurs jeux de résultats, la méthode <xref:System.Data.DataTableReader.NextResult%2A> déplace le curseur sur le jeu de résultats suivant. Il s'agit d'un processus en avant uniquement. Il n'est pas possible de revenir à un jeu de résultats précédent.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `TestConstructor` méthode crée deux <xref:System.Data.DataTable> instances. Afin d’illustrer ce constructeur pour la <xref:System.Data.DataTableReader> classe, l’exemple crée un objet **DataTableReader** basé sur un tableau qui contient les deux **DataTables**, et effectue une opération simple, en imprimant le contenu à partir des quelques premières colonnes dans la fenêtre de console.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [DataTableReaders](datatablereaders.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
