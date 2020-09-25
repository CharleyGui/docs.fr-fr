---
title: Activation d'une source de données pour l'interrogation LINQ
description: Découvrez comment étendre LINQ en C# pour permettre l’interrogation de toute source de données dans le modèle LINQ, ce qui permet aux clients d’interroger facilement une source de données.
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: d7d751c0584072e740b4e5292071e400a5020f82
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202615"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Activation d'une source de données pour l'interrogation LINQ

Il existe plusieurs façons d’étendre LINQ pour permettre l’interrogation de toute source de données dans le modèle LINQ. La source de données peut être une structure de données, un service Web, un système de fichiers ou une base de données, par exemple. Le modèle LINQ permet aux clients d’interroger facilement une source de données pour laquelle l’interrogation LINQ est activée, car la syntaxe et le modèle de la requête ne changent pas. Les façons dont LINQ peut être étendu à ces sources de données sont les suivantes :  
  
- Implémentation de l' <xref:System.Collections.Generic.IEnumerable%601> interface dans un type pour permettre LINQ to Objects interrogation de ce type.  
  
- Création de méthodes d’opérateur de requête standard telles que <xref:System.Linq.Enumerable.Where%2A> et <xref:System.Linq.Enumerable.Select%2A> qui étendent un type, pour activer l’interrogation LINQ personnalisée de ce type.  
  
- Création d'un fournisseur pour votre source de données qui implémente l'interface <xref:System.Linq.IQueryable%601>. Un fournisseur qui implémente cette interface reçoit des requêtes LINQ sous la forme d’arborescences d’expression, qu’il peut exécuter de façon personnalisée, par exemple à distance.  
  
- Création d’un fournisseur pour votre source de données qui tire parti d’une technologie LINQ existante. Ce type de fournisseur permettrait non seulement l'interrogation, mais également l'insertion, la mise à jour et la suppression d'opérations et le mappage pour des types définis par l'utilisateur.  
  
 Cette rubrique décrit ces options.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Comment activer l'interrogation LINQ de votre source de données  
  
### <a name="in-memory-data"></a>Données en mémoire  

 Vous pouvez activer l’interrogation LINQ des données en mémoire de deux manières. Si les données sont d’un type qui implémente <xref:System.Collections.Generic.IEnumerable%601> , vous pouvez interroger les données à l’aide de LINQ to Objects. S’il est inutile d’activer l’énumération de votre type en implémentant l' <xref:System.Collections.Generic.IEnumerable%601> interface, vous pouvez définir des méthodes d’opérateur de requête standard LINQ dans ce type ou créer des méthodes d’opérateur de requête standard LINQ qui étendent le type. Les implémentations personnalisées des opérateurs de requête standard doivent utiliser l'exécution différée pour retourner les résultats.  
  
### <a name="remote-data"></a>Données distantes  

 La meilleure option pour activer l’interrogation LINQ d’une source de données distante est d’implémenter l' <xref:System.Linq.IQueryable%601> interface. Toutefois, cette méthode diffère de l'extension d'un fournisseur tel que [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pour une source de données. Aucun modèle de fournisseur pour l’extension des technologies LINQ existantes, tel que [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , à d’autres types de source de données n’est disponible dans Visual Studio 2008.
  
## <a name="iqueryable-linq-providers"></a>Fournisseurs LINQ IQueryable  

 Les fournisseurs LINQ qui implémentent <xref:System.Linq.IQueryable%601> peuvent varier considérablement dans leur complexité. Cette section décrit les différents niveaux de complexité.  
  
 Un fournisseur `IQueryable` moins complexe peut interagir avec une méthode unique d'un service Web. Ce type de fournisseur est très particulier, car il attend des informations spécifiques dans les requêtes qu'il gère. Il se caractérise par un système de type fermé, exposant peut-être un type de résultat unique. La plus grande part de l'exécution de la requête est effectuée localement, par exemple à l'aide des implémentations <xref:System.Linq.Enumerable> des opérateurs de requête standard. Un fournisseur moins complexe peut examiner une seule expression d'appel de méthode dans l'arborescence d'expression qui représente la requête, et la logique restante de la requête doit être gérée ailleurs.  
  
 Un fournisseur `IQueryable` de complexité moyenne peut cibler une source de données qui possède un langage de requête partiellement expressif. S'il cible un service Web, il peut interagir avec plusieurs méthodes du service Web et sélectionner la méthode d'appel en fonction de la question posée par la requête. Un fournisseur de complexité moyenne aurait un système plus sophistiqué que celui d'un fournisseur simple, qui serait néanmoins un système de type fixe. Par exemple, le fournisseur peut exposer des types qui ont des relations un-à-plusieurs qui peuvent être parcourues, mais il ne fournirait pas de technologie de mappage pour les types définis par l'utilisateur.  
  
 Un `IQueryable` fournisseur complexe, tel que le [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] fournisseur, peut traduire des requêtes LINQ complètes en un langage de requête expressif, tel que SQL. Un fournisseur complexe est plus général qu'un fournisseur moins complexe, car il peut gérer une plus grande gamme de questions dans la requête. Il possède également un système de type ouvert et doit donc contenir une infrastructure étendue pour mapper les types définis par l'utilisateur. Développer un fournisseur complexe est une tâche difficile.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Présentation des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
