---
title: Mappages de types personnalisés SQL-CLR
ms.date: 03/30/2017
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
ms.openlocfilehash: 14d7f8409f93a5414a37a8b1c8e172f53478e817
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155703"
---
# <a name="sql-clr-custom-type-mappings"></a>Mappages de types personnalisés SQL-CLR

Le mappage de type entre SQL Server et le langage Common Language Runtime (CLR) est automatiquement spécifié lorsque vous utilisez l'outil de ligne de commande SQLMetal ou le Concepteur Objet/Relationnel (Concepteur O/R).  
  
 Quand aucun mappage personnalisé n’est effectué, ces outils assignent des mappages de types par défaut, comme décrit dans [mappage de type SQL-CLR](sql-clr-type-mapping.md). Si vous souhaitez que les mappages de types s'effectuent différemment de ceux par défaut, vous devez les personnaliser.  
  
 Lors de la personnalisation des mappages de types, l'approche recommandée consiste à modifier un fichier DBML intermédiaire. Vous devez ensuite utiliser ce fichier DBML personnalisé lorsque vous créez les fichiers de code et de mappage à l'aide de SQLMetal ou du Concepteur O/R.  
  
 Après avoir instancié l'objet <xref:System.Data.Linq.DataContext> à partir des fichiers de code et de mappage, la méthode <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> crée une base de données en fonction des mappages de types spécifiés. En l'absence d'attributs `type` CLR spécifié dans les mappages, les mappages de types par défaut sont utilisés.  
  
## <a name="customization-with-sqlmetal-or-or-designer"></a>Personnalisation à l'aide de SQLMetal ou du Concepteur O/R  

 SQLMetal et le Concepteur O/R vous permettent de créer automatiquement un modèle objet qui inclut les informations de mappage de type à l'intérieur ou à l'extérieur du fichier de code. Ces fichiers étant remplacés par SQLMetal ou le Concepteur O/R, chaque fois que vous recréez vos mappages, l'approche recommandée en termes de spécification de mappages de types personnalisés consiste à personnaliser un fichier DBML.  
  
 Pour personnaliser des mappages de types à l'aide de SQLMetal ou du Concepteur OR, commencez par générer un fichier DBML. Puis, avant de générer le fichier de code ou de mappage, modifiez ce fichier DBML de façon à identifier les mappages de types souhaités. Si vous utilisez SQLMetal, vous devez modifier manuellement les attributs `Type` et `DbType` dans le fichier DBML pour personnaliser les mappages de types. Si vous utilisez le Concepteur O/R, vous pouvez apporter vos modifications dans celui-ci. Pour plus d’informations sur l’utilisation du Concepteur O/R, consultez [LINQ to SQL Tools dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
> [!NOTE]
> Certains mappages de types peuvent entraîner des exceptions de dépassement de capacité ou de perte de données lors de la traduction à partir de la base de données ou vers celle-ci. Examinez attentivement la matrice de comportement au moment de l’exécution du mappage de type dans le [mappage de type SQL-CLR](sql-clr-type-mapping.md) avant d’effectuer des personnalisations.  
  
 Pour que SQLMetal ou le Concepteur O/R reconnaisse les personnalisations de mappage de type, vous devez vous assurer que ces outils incluent le chemin d'accès à votre fichier DBML personnalisé lorsque vous générez le fichier de code ou de mappage externe. Même si cela n'est pas requis dans le cadre de la personnalisation de mappage de type, nous vous recommandons de séparer systématiquement les informations de mappage de type du fichier de code et de générer le fichier de mappage externe supplémentaire. Cela offre une certaine souplesse en vous évitant d'avoir à recompiler le fichier de code.  
  
## <a name="incorporating-database-changes"></a>Intégration des modifications de base de données  

 En cas de modification de la base de données, vous devez mettre à jour le fichier DBML afin qu'il prenne ces modifications en compte. L'une des méthodes utilisées consiste à créer automatiquement un nouveau fichier DBML et à effectuer de nouveau les personnalisations de mappage de type. Vous pouvez aussi comparer les différences entre le nouveau fichier DBML et le fichier DBML personnalisé, puis mettre ce dernier à jour manuellement afin de prendre en compte les modifications de base de données.  
  
## <a name="see-also"></a>Voir aussi

- [Mappage de type SQL-CLR](sql-clr-type-mapping.md)
- [Génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md)
