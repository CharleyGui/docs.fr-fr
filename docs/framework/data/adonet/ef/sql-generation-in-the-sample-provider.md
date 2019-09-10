---
title: Génération SQL dans le Fournisseur d'exemples
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854319"
---
# <a name="sql-generation-in-the-sample-provider"></a>Génération SQL dans le Fournisseur d'exemples
L' [exemple de fournisseur Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) illustre les nouveaux composants des fournisseurs de données ADO.net qui prennent en charge l’Entity Framework.  Il utilise une base de données SQL Server 2005 et est implémenté comme un wrapper pour le fournisseur de données System.Data.SqlClient ADO.NET 2.0.  
  
 Le module Génération SQL du Fournisseur d’exemples (situé sous le dossier Génération SQL, à l’exception du fichier DmlSqlGenerator.cs) prend un DbQueryCommandTree d’entrée et produit une instruction SQL SELECT unique.  
  
## <a name="in-this-section"></a>Dans cette section  
 Cette section comprend les rubriques suivantes :  
  
 [Architecture et conception](architecture-and-design.md)  
  
 [Procédure pas à pas : Génération SQL](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Voir aussi

- [Génération SQL](sql-generation.md)
