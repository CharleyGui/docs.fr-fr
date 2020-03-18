---
title: Activation d'une source de données pour l'interrogation LINQ
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 9a143f0da74d4e91ef697f468d7fda225e75245b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635767"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Activation d'une source de données pour l'interrogation LINQ
Il existe différentes façons d’étendre le LINQ pour permettre à toute source de données d’être interrogée dans le modèle LINQ. La source de données peut être une structure de données, un service Web, un système de fichiers ou une base de données, par exemple. Le modèle LINQ permet aux clients d’interroger facilement une source de données pour laquelle la requête LINQ est activée, car la syntaxe et le modèle de la requête ne changent pas. La façon dont LINQ peut être étendue à ces sources de données est la suivante :  
  
- Mise en <xref:System.Collections.Generic.IEnumerable%601> œuvre de l’interface en un type pour permettre à LINQ d’interroger les objets de ce type.  
  
- Création de méthodes standard <xref:System.Linq.Enumerable.Where%2A> d’opérateur de requête telles que et <xref:System.Linq.Enumerable.Select%2A> qui étendent un type, pour permettre la requête personnalisée LINQ de ce type.  
  
- Création d'un fournisseur pour votre source de données qui implémente l'interface <xref:System.Linq.IQueryable%601>. Un fournisseur qui implémente cette interface reçoit des requêtes LINQ sous forme d’arbres d’expression, qu’il peut exécuter de manière personnalisée, par exemple à distance.  
  
- Créer un fournisseur pour votre source de données qui tire parti d’une technologie LINQ existante. Ce type de fournisseur permettrait non seulement l'interrogation, mais également l'insertion, la mise à jour et la suppression d'opérations et le mappage pour des types définis par l'utilisateur.  
  
 Cette rubrique décrit ces options.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Comment activer l'interrogation LINQ de votre source de données  
  
### <a name="in-memory-data"></a>Données en mémoire  
 Il y a deux façons d’activer la requête LINQ des données en mémoire. Si les données sont d’un type qui implémente, <xref:System.Collections.Generic.IEnumerable%601>vous pouvez interroger les données en utilisant LINQ à des objets. S’il n’est pas logique d’activer votre <xref:System.Collections.Generic.IEnumerable%601> type en implémentant l’interface, vous pouvez définir les méthodes d’opérateur de requête standard LINQ dans ce type ou créer des méthodes d’opérateur de requête standard LINQ qui étendent le type. Les implémentations personnalisées des opérateurs de requête standard doivent utiliser l'exécution différée pour retourner les résultats.  
  
### <a name="remote-data"></a>Données distantes  
 La meilleure option pour permettre à LINQ de poser <xref:System.Linq.IQueryable%601> des questions sur une source de données à distance est de mettre en œuvre l’interface. Toutefois, cette méthode diffère de l'extension d'un fournisseur tel que [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pour une source de données. Aucun modèle de fournisseur pour étendre [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]les technologies LINQ existantes, comme , à d’autres types de sources de données n’est disponible dans Visual Studio 2008.
  
## <a name="iqueryable-linq-providers"></a>Fournisseurs LINQ IQueryable  
 Les fournisseurs de <xref:System.Linq.IQueryable%601> LINQ qui mettent en œuvre peuvent varier considérablement dans leur complexité. Cette section décrit les différents niveaux de complexité.  
  
 Un fournisseur `IQueryable` moins complexe peut interagir avec une méthode unique d'un service Web. Ce type de fournisseur est très particulier, car il attend des informations spécifiques dans les requêtes qu'il gère. Il se caractérise par un système de type fermé, exposant peut-être un type de résultat unique. La plus grande part de l'exécution de la requête est effectuée localement, par exemple à l'aide des implémentations <xref:System.Linq.Enumerable> des opérateurs de requête standard. Un fournisseur moins complexe peut examiner une seule expression d'appel de méthode dans l'arborescence d'expression qui représente la requête, et la logique restante de la requête doit être gérée ailleurs.  
  
 Un fournisseur `IQueryable` de complexité moyenne peut cibler une source de données qui possède un langage de requête partiellement expressif. S'il cible un service Web, il peut interagir avec plusieurs méthodes du service Web et sélectionner la méthode d'appel en fonction de la question posée par la requête. Un fournisseur de complexité moyenne aurait un système plus sophistiqué que celui d'un fournisseur simple, qui serait néanmoins un système de type fixe. Par exemple, le fournisseur peut exposer des types qui ont des relations un-à-plusieurs qui peuvent être parcourues, mais il ne fournirait pas de technologie de mappage pour les types définis par l'utilisateur.  
  
 Un `IQueryable` fournisseur complexe, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] comme le fournisseur, peut traduire des requêtes complètes de LINQ dans un langage de requête expressif, comme SQL. Un fournisseur complexe est plus général qu'un fournisseur moins complexe, car il peut gérer une plus grande gamme de questions dans la requête. Il possède également un système de type ouvert et doit donc contenir une infrastructure étendue pour mapper les types définis par l'utilisateur. Développer un fournisseur complexe est une tâche difficile.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
