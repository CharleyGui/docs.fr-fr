---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: b0660312f540a69911905edd08541ed70cf39bb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174314"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]est un composant de la version cadre .NET 3.5 qui fournit une infrastructure de temps d’exécution pour la gestion des données relationnelles comme des objets.  
  
> [!NOTE]
> Les données relationnelles apparaissent comme une collection de tables à deux dimensions (*relations* ou *fichiers plats*) où des colonnes communes relient les tables entre elles. Pour utiliser efficacement [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous devez posséder quelques connaissances des principes sous-jacents des bases de données relationnelles.  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], le modèle de données d’une base de données relationnelle est mappé à un modèle objet exprimé dans le langage de programmation du développeur. Lors de l'exécution de l'application, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit des requêtes LINQ dans le modèle objet en SQL et les envoie à la base de données pour exécution. Lorsque la base de données retourne les résultats, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les traduit en objets que vous pouvez utiliser dans votre propre langage de programmation.  
  
 Les développeurs utilisant Visual Studio utilisent généralement l’object Relational Designer, qui [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]fournit une interface utilisateur pour la mise en œuvre de nombreuses fonctionnalités de .  
  
 La documentation incluse avec cette mise en production de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] décrit les blocs de construction de base, les processus et les techniques dont vous avez besoin pour générer des applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Vous pouvez également rechercher Microsoft Docs pour des questions spécifiques, et vous pouvez participer au [Forum LINQ](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), où vous pouvez discuter de sujets plus complexes en détail avec des experts. Enfin, le [LINQ à SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, avec des exemples de code Visual Basic et C.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](getting-started.md)  
 Fournit une vue d’ensemble de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et des informations pour se familiariser avec l’utilisation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Guide de programmation](programming-guide.md)  
 Explique comment effectuer les tâches de mappage, d’interrogation, de mise à jour, de débogage et d’autres tâches de ce type.  
  
 [Référence](reference.md)  
 Fournit des informations de référence sur plusieurs aspects de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Les rubriques incluent le mappage de type CLR-SQL, la traduction d'opérateur de requête standard, etc.  
  
 [Exemples](samples.md)  
 Fournit des liens vers des échantillons visual basic et C.  
  
## <a name="related-sections"></a>Sections connexes  
 [Requête linguistique intégrée (LINQ) - C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Fournit des aperçus des technologies LINQ en C.

 [LINQ (Language-Integrated Query) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fournit des aperçus des technologies LINQ dans Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Décrit les technologies LINQ pour les utilisateurs de Visual Basic.  
  
 [LINQ et ADO.NET](../../linq-and-ado-net.md)  
 Liens vers le portail ADO.NET.  
  
 [Procédures pas à pas LINQ to SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Répertorie les procédures pas à pas disponibles pour [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Téléchargement d’exemples de base de données](downloading-sample-databases.md)  
 Explique comment télécharger les exemples de base de données utilisés dans la documentation.  
  
 [Aperçu du contrôle du serveur Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Décrit comment <xref:System.Web.UI.WebControls.LinqDataSource> le contrôle expose la requête intégrée par la langue (LINQ) aux développeurs Web par l’intermédiaire de l’architecture de contrôle des sources de données ASP.NET.
