---
title: Génération SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854355"
---
# <a name="sql-generation"></a>Génération SQL
Lorsque vous écrivez un fournisseur pour le Entity Framework, vous devez traduire Entity Framework arborescences de commandes en SQL qu’une base de données spécifique peut comprendre, comme Transact-SQL pour SQL Server ou PL/SQL pour Oracle. Dans cette section, vous allez apprendre à développer un composant de génération SQL (pour les requêtes SELECT) pour un fournisseur Entity Framework. Pour plus d’informations sur les requêtes d’insertion, de mise à jour et de suppression, consultez Modification de la [génération SQL](modification-sql-generation.md).  
  
 Pour comprendre cette section, vous devez connaître les Entity Framework et le modèle de fournisseur ADO.NET. Vous devez également comprendre les arborescences de commandes et les <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Rôle du module de génération SQL  
 Le module de génération SQL d’un fournisseur de Entity Framework traduit une arborescence de commandes de requête donnée en une instruction SQL SELECT unique qui cible une base de données conforme SQL : 1999. Le SQL généré doit avoir aussi peu de requêtes imbriquées que possible. Le module de génération SQL ne doit pas simplifier l’arborescence de commandes de requête de sortie. La Entity Framework effectue cette opération, par exemple en éliminant les jointures et en réduisant les nœuds de filtre consécutifs.  
  
 La classe <xref:System.Data.Common.DbProviderServices> est le point de départ permettant d’accéder à la couche de génération SQL pour convertir des arborescences de commandes en <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Forme des arborescences de commandes](the-shape-of-the-command-trees.md)  
  
 [Génération SQL à partir d’arborescences de commandes - Bonnes pratiques](generating-sql-from-command-trees-best-practices.md)  
  
 [Génération SQL dans l’exemple de fournisseur](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Voir aussi

- [Écriture d’un fournisseur de données Entity Framework](writing-an-ef-data-provider.md)
