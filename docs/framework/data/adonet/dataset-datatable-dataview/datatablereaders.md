---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 911a45dad3d5d82ab5e5752b1c12f7d8a6ab1563
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202316"
---
# <a name="datatablereaders"></a>DataTableReaders

L'objet <xref:System.Data.DataTableReader> présente le contenu d'un objet <xref:System.Data.DataTable> ou d'un objet <xref:System.Data.DataSet> sous la forme d'un ou plusieurs jeux de résultats en lecture seule et en avant uniquement.  
  
 Quand vous créez un **DataTableReader** à partir d’un **DataTable**, l’objet **DataTableReader** résultant contient un jeu de résultats avec les mêmes données que le **DataTable** à partir duquel il a été créé, à l’exception des lignes qui ont été marquées comme supprimées. Les colonnes apparaissent dans le même ordre que dans le **DataTable**d’origine.  
  
 Un **DataTableReader** peut contenir plusieurs jeux de résultats s’il a été créé en appelant <xref:System.Data.DataSet.CreateDataReader%2A> . Les résultats sont dans le même ordre que les **DataTables** dans la collection de l’objet **DataSet** <xref:System.Data.DataSet.Tables%2A> .  
  
## <a name="in-this-section"></a>Dans cette section  

 [Création d'un DataReader](creating-a-datareader.md)  
 Explique comment créer un objet **DataTableReader** .  
  
 [Navigation sur les DataTable](navigating-datatables.md)  
 Décrit l’utilisation de la méthode **Read** pour parcourir le contenu d’un **DataTableReader**.  
  
## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](../retrieving-and-modifying-data.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
