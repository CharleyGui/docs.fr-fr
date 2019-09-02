---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203819"
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
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
