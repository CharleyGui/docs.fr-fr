---
title: 'Procédure : Générer le modèle objet en Visual Basic ou en C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: e2491cf18be556cb26f084a178b7bf09448c6904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546612"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Comment : générer le modèle objet dans Visual Basic ou C\#
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle. Deux outils sont disponibles pour générer automatiquement un modèle Visual Basic ou C# à partir des métadonnées d’une base de données existante.  
  
- Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour générer un modèle objet. Le Concepteur O/R fournit une interface utilisateur riche pour vous aider à générer un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modèle d’objet. Pour plus d’informations, consultez [Outils LINQ to SQL dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- Outil en ligne de commande SQLMetal Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Pour plus d’informations, consultez [Comment : créer dynamiquement une base de données](how-to-dynamically-create-a-database.md).  
  
 La documentation du Concepteur O/R fournit des exemples de génération d’un Visual Basic ou d’un modèle objet C# à l’aide du Concepteur O/R. Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a> Exemple  
 La ligne de commande SQLMetal présentée dans l’exemple suivant produit Visual Basic code comme modèle objet basé sur les attributs de l’exemple de base de données Northwind. Des procédures stockées et des fonctions sont également restituées.  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a> Exemple  
 La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind. Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](programming-guide.md)
- [Modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)
- [Apprentissage par les procédures pas à pas](learning-by-walkthroughs.md)
- [Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mappage basé sur les attributs](attribute-based-mapping.md)
- [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Mappage externe](external-mapping.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
- [Création du modèle objet](creating-the-object-model.md)
