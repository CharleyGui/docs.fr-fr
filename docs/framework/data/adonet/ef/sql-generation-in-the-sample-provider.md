---
title: Génération SQL dans le Fournisseur d'exemples
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248509"
---
# <a name="sql-generation-in-the-sample-provider"></a>Génération SQL dans le Fournisseur d'exemples
L' [exemple de fournisseur Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) illustre les nouveaux composants des fournisseurs de données ADO.net qui [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]prennent en charge.  Il utilise une base de données SQL Server 2005 et est implémenté comme un wrapper pour le fournisseur de données System.Data.SqlClient ADO.NET 2.0.  
  
 Le module Génération SQL du Fournisseur d’exemples (situé sous le dossier Génération SQL, à l’exception du fichier DmlSqlGenerator.cs) prend un DbQueryCommandTree d’entrée et produit une instruction SQL SELECT unique.  
  
## <a name="in-this-section"></a>Dans cette section  
 Cette section comprend les rubriques suivantes :  
  
 [Architecture et conception](architecture-and-design.md)  
  
 [Procédure pas à pas : Génération SQL](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Voir aussi

- [Génération SQL](sql-generation.md)
