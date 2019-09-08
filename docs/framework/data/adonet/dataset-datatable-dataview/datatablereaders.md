---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785343"
---
# <a name="datatablereaders"></a>DataTableReaders
L'objet <xref:System.Data.DataTableReader> présente le contenu d'un objet <xref:System.Data.DataTable> ou d'un objet <xref:System.Data.DataSet> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.  
  
 Quand vous créez un **DataTableReader** à partir d’un **DataTable**, l’objet **DataTableReader** résultant contient un jeu de résultats avec les mêmes données que le **DataTable** à partir duquel il a été créé, à l’exception des lignes qui ont été marquées comme supprimé. Les colonnes apparaissent dans le même ordre que dans le **DataTable**d’origine.  
  
 Un **DataTableReader** peut contenir plusieurs jeux de résultats s’il a été créé <xref:System.Data.DataSet.CreateDataReader%2A>en appelant. Les résultats sont dans le même ordre que les **DataTables** dans la collection de <xref:System.Data.DataSet.Tables%2A> l’objet DataSet.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un DataReader](creating-a-datareader.md)  
 Explique comment créer un objet **DataTableReader** .  
  
 [Navigation dans les DataTables](navigating-datatables.md)  
 Décrit l’utilisation de la méthode **Read** pour parcourir le contenu d’un **DataTableReader**.  
  
## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](../retrieving-and-modifying-data.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
