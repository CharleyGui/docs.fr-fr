---
title: LINQ to SQL
description: LINQ to SQL est un composant du .NET Framework qui fournit une infrastructure runtime pour gérer des données relationnelles en tant qu’objets.
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: d6fadecf17cae21527cec2180b6d6c5b5e85d0cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551312"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est un composant de .NET Framework version 3,5 qui fournit une infrastructure runtime pour la gestion des données relationnelles en tant qu’objets.  
  
> [!NOTE]
> Les données relationnelles apparaissent comme une collection de tables à deux dimensions (*relations* ou *fichiers plats*) où des colonnes communes relient les tables entre elles. Pour utiliser efficacement [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous devez posséder quelques connaissances des principes sous-jacents des bases de données relationnelles.  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], le modèle de données d’une base de données relationnelle est mappé à un modèle objet exprimé dans le langage de programmation du développeur. Lors de l'exécution de l'application, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit des requêtes LINQ dans le modèle objet en SQL et les envoie à la base de données pour exécution. Lorsque la base de données retourne les résultats, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les traduit en objets que vous pouvez utiliser dans votre propre langage de programmation.  
  
 Les développeurs qui utilisent Visual Studio utilisent généralement le Concepteur Objet Relationnel, qui fournit une interface utilisateur pour l’implémentation de nombreuses fonctionnalités de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 La documentation incluse avec cette mise en production de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] décrit les blocs de construction de base, les processus et les techniques dont vous avez besoin pour générer des applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Vous pouvez également rechercher des problèmes spécifiques dans Microsoft Docs, et vous pouvez participer au [Forum LINQ](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), où vous pouvez aborder des sujets plus complexes avec des experts. Enfin, le livre blanc [LINQ to SQL : LINQ (Language-Integrated Query) .net pour les données relationnelles](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) décrit en détail la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie, ainsi que des exemples de code Visual Basic et C#.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](getting-started.md)  
 Fournit une vue d’ensemble de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et des informations pour se familiariser avec l’utilisation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Guide de programmation](programming-guide.md)  
 Explique comment effectuer les tâches de mappage, d’interrogation, de mise à jour, de débogage et d’autres tâches de ce type.  
  
 [Référence](reference.md)  
 Fournit des informations de référence sur plusieurs aspects de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Les rubriques incluent le mappage de type CLR-SQL, la traduction d'opérateur de requête standard, etc.  
  
 [Exemples](samples.md)  
 Fournit des liens vers des exemples Visual Basic et C#.  
  
## <a name="related-sections"></a>Sections connexes  
 [LINQ (Language-Integrated Query)-C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Fournit des vues d’ensemble des technologies LINQ en C#.

 [LINQ (Language-Integrated Query) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fournit des vues d’ensemble des technologies LINQ dans Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Décrit les technologies LINQ pour les utilisateurs de Visual Basic.  
  
 [LINQ et ADO.NET](../../linq-and-ado-net.md)  
 Liens vers le portail ADO.NET.  
  
 [Procédures pas à pas LINQ to SQL](/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Répertorie les procédures pas à pas disponibles pour [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Téléchargement d’exemples de base de données](downloading-sample-databases.md)  
 Explique comment télécharger les exemples de base de données utilisés dans la documentation.  
  
 [Vue d’ensemble du contrôle serveur Web LinqDataSource](/previous-versions/aspnet/bb547113(v=vs.100))  
 Décrit comment le <xref:System.Web.UI.WebControls.LinqDataSource> contrôle expose LINQ (Language-Integrated Query) aux développeurs Web via l’architecture de contrôle de source de données ASP.net.
