---
title: 'Procédure : Générer du code personnalisé en modifiant un fichier DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 01890e6b899db6b70049e2d6b8193e5b0f4095fb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781983"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Procédure : Générer du code personnalisé en modifiant un fichier DBML
Vous pouvez générer des Visual Basic C# ou du code source à partir d’un fichier de métadonnées. dbml (Database Markup Language). Cette approche permet de personnaliser le fichier .dbml par défaut avant de générer le code de mappage de l’application. Il s'agit d'une fonctionnalité avancée.  
  
 Les étapes de ce processus sont les suivantes :  
  
1. Générez un fichier .dbml.  
  
2. Utilisez un éditeur pour modifier le fichier .dbml. Notez que le fichier. dbml doit être validé par rapport au fichier de définition de schéma ( [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . xsd) pour les fichiers. dbml. Pour plus d’informations, consultez [génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md).  
  
3. Générez le Visual Basic C# ou le code source.  
  
 Les exemples suivants utilisent l'outil en ligne de commande SQLMetal. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemples  
 Le code suivant génère un fichier .dbml à partir de l'exemple de base de données Northwind. Vous pouvez utiliser le nom de la base de données ou le nom du fichier .mdf comme source pour les métadonnées de base de données.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Exemples  
 Le code suivant génère Visual Basic ou C# un fichier de code source à partir d’un fichier. dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Voir aussi

- [Génération de code dans LINQ to SQL](code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Création du modèle objet](creating-the-object-model.md)
