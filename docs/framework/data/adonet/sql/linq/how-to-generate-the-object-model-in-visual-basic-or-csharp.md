---
title: 'Procédure : Générer le modèle objet en Visual Basic ou en C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 24b48b4962ac207f0c6a50456797ff588a97082d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743312"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Procédure : Générer le modèle objet en Visual Basic ou C\#
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle. Deux outils sont disponibles pour générer automatiquement un Visual Basic ou C# modèle à partir des métadonnées de base de données existante.  
  
- Si vous utilisez Visual Studio, vous pouvez utiliser le concepteur objet/relationnel pour générer un modèle objet. Le Concepteur O/R fournit une interface utilisateur élaborée pour vous aider à générer un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modèle objet. Pour plus d’informations, consultez [outils Linq to SQL dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- Outil en ligne de commande SQLMetal Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Pour plus d’informations, consultez [Guide pratique pour Créer dynamiquement une base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Documentation pour le Concepteur O/R fournit des exemples montrant comment générer un Visual Basic ou C# modèle d’objet à l’aide du Concepteur O/R. Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemple  
 La ligne de commande SQLMetal présentée dans l’exemple suivant génère le code Visual Basic en tant que le modèle objet basé sur un attribut de la base de données Northwind. Des procédures stockées et des fonctions sont également restituées.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Exemple  
 La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind. Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Guide pratique : Personnaliser des Classes d’entité à l’aide de l’éditeur de Code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mappage basé sur les attributs](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
