---
title: Analyse du code source LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 4b23e0df1ee762dd22d43cd1be050db70481db50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964111"
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analyse du code source LINQ to SQL
En exécutant les étapes suivantes, vous pouvez générer le code source [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à partir de l'exemple de base de données Northwind. Vous pouvez comparer des éléments du modèle objet avec des éléments de la base de données pour mieux comprendre comment les différents éléments sont mappés.  
  
> [!NOTE]
> Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur O/R pour générer ce code.  
  
1. Si vous n'avez pas déjà l'exemple de base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger gratuitement. Pour plus d’informations, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2. Utilisez l'outil en ligne de commande SQLMetal pour générer un fichier source Visual Basic ou C#. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). En tapant les commandes suivantes à une invite de commandes, vous pouvez générer les fichiers sources Visual Basic et C# qui incluent des procédures stockées et des fonctions :  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Voir aussi

- [Référence](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
