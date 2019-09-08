---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: fbb2f8cf37bd05864dc93b8ebbd33466a9a2c55e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793080"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]est un composant de .NET Framework version 3,5 qui fournit une infrastructure runtime pour la gestion des données relationnelles en tant qu’objets.  
  
> [!NOTE]
> Les données relationnelles apparaissent comme une collection de tables à deux dimensions (*relations* ou *fichiers plats*) où des colonnes communes relient les tables entre elles. Pour utiliser efficacement [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous devez posséder quelques connaissances des principes sous-jacents des bases de données relationnelles.  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], le modèle de données d’une base de données relationnelle est mappé à un modèle objet exprimé dans le langage de programmation du développeur. Lors de l'exécution de l'application, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit des requêtes LINQ dans le modèle objet en SQL et les envoie à la base de données pour exécution. Lorsque la base de données retourne les résultats, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les traduit en objets que vous pouvez utiliser dans votre propre langage de programmation.  
  
 Les développeurs qui utilisent Visual Studio utilisent généralement le Concepteur Objet Relationnel, qui fournit une interface utilisateur pour l’implémentation de nombreuses [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]fonctionnalités de.  
  
 La documentation incluse avec cette mise en production de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] décrit les blocs de construction de base, les processus et les techniques dont vous avez besoin pour générer des applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Vous pouvez également rechercher des problèmes spécifiques dans Microsoft Docs, et vous pouvez participer au [Forum LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), où vous pouvez aborder des sujets plus complexes avec des experts. Enfin, le livre blanc [LINQ to SQL : langage .net LINQ for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) est détaillé [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] avec Visual Basic et C# des exemples de code.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](getting-started.md)  
 Fournit une vue d’ensemble de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et des informations pour se familiariser avec l’utilisation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Guide de programmation](programming-guide.md)  
 Explique comment effectuer les tâches de mappage, d’interrogation, de mise à jour, de débogage et d’autres tâches de ce type.  
  
 [Référence](reference.md)  
 Fournit des informations de référence sur plusieurs aspects de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Les rubriques incluent le mappage de type CLR-SQL, la traduction d'opérateur de requête standard, etc.  
  
 [Exemples](samples.md)  
 Fournit des liens vers des C# Visual Basic et des exemples.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [LINQ (Language-Integrated Query)-C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Fournit des vues d’ensemble des technologies LINQ C#dans.
 
 [LINQ (Language-Integrated Query) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fournit des vues d’ensemble des technologies LINQ dans Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Décrit [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] les technologies pour les utilisateurs de Visual Basic.  
  
 [LINQ et ADO.NET](../../linq-and-ado-net.md)  
 Liens vers le portail ADO.NET.  
  
 [Procédures pas à pas LINQ to SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Répertorie les procédures pas à pas disponibles pour [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Téléchargement d’exemples de base de données](downloading-sample-databases.md)  
 Explique comment télécharger les exemples de base de données utilisés dans la documentation.  
  
 [Vue d’ensemble du contrôle serveur Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Décrit comment le <xref:System.Web.UI.WebControls.LinqDataSource> contrôle [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] expose aux développeurs Web via l’architecture de contrôle de source de données ASP.net.
