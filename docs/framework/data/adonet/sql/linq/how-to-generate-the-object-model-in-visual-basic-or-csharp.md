---
title: 'Procédure : Générer le modèle objet en Visual Basic ou en C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 5f2c2f99a5efeb3463ecf5bf401a6cf654845bb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911966"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Procédure : Générer le modèle objet dans Visual Basic ou C\#
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle. Deux outils sont disponibles pour générer automatiquement une Visual Basic ou C# un modèle à partir des métadonnées d’une base de données existante.  
  
- Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour générer un modèle objet. Le Concepteur O/R fournit une interface utilisateur riche pour vous aider à générer [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] un modèle d’objet. Pour plus d’informations, consultez [Outils LINQ to SQL dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- Outil en ligne de commande SQLMetal Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Pour plus d’informations, consultez [Guide pratique pour Créer dynamiquement une base](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)de données.  
  
 La documentation relative au Concepteur O/R fournit des exemples de génération d’un Visual Basic C# ou d’un modèle objet à l’aide du concepteur o/r. Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemples  
 La ligne de commande SQLMetal présentée dans l’exemple suivant produit Visual Basic code comme modèle objet basé sur les attributs de l’exemple de base de données Northwind. Des procédures stockées et des fonctions sont également restituées.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Exemples  
 La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind. Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mappage basé sur les attributs](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
