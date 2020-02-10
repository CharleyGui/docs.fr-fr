---
title: LINQ et ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: c5b56fa78ce0276953597d63b3d6e2f45d88c8ab
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094434"
---
# <a name="linq-and-adonet"></a>LINQ et ADO.NET

Aujourd’hui, de nombreux développeurs professionnels doivent utiliser deux langages de programmation (ou plus) : un langage de haut niveau pour la logique métier et les couches de C# présentation (par exemple, Visual ou Visual Basic) et un langage de requête pour interagir avec la base de données (par exemple, Transact-SQL). Pour être efficace, le développeur doit être expert en plusieurs langages, et cela peut entraîner des incompatibilités dans l'environnement de développement. Par exemple, une application qui utilise une API d'accès aux données pour exécuter une requête sur une base de données spécifie la requête comme un littéral de chaîne en utilisant des guillemets. Cette chaîne de requête est illisible pour le compilateur et n’est pas vérifiée pour rechercher des erreurs, telles qu’une syntaxe non valide, ou si les colonnes ou les lignes qu’elle référence existent réellement. Il n'y a aucune vérification de type des paramètres de requête et aucune prise en charge `IntelliSense`.  
  
 LINQ (Language-Integrated Query) permet aux développeurs de former des requêtes basées sur des ensembles dans leur code d’application, sans avoir à utiliser un langage de requête séparé. Vous pouvez écrire des requêtes LINQ sur différentes sources de données énumérables (autrement dit, une source de données qui implémente l’interface <xref:System.Collections.IEnumerable>), telles que des structures de données en mémoire, des documents XML, des bases de données SQL et des objets <xref:System.Data.DataSet>. Bien que ces sources de données énumérables soient implémentées de diverses manières, elles exposent toutes la même syntaxe et les mêmes constructions de langage. Parce que les requêtes peuvent être formées à même le langage de programmation, vous n'avez pas à utiliser un autre langage de requêtes intégré en tant que littéraux de chaîne et qui ne peut pas être compris ou vérifié par le compilateur. L’intégration des requêtes dans le langage de programmation permet également aux programmeurs Visual Studio d’être plus productifs en fournissant la vérification de la syntaxe et du type au moment de la compilation, et `IntelliSense`. Ces fonctionnalités réduisent la nécessité du débogage de requête et de la résolution d'erreur.  
  
 Le transfert des données à partir des tables SQL dans des objets en mémoire est souvent fastidieux et susceptible d'engendrer des erreurs. Le fournisseur LINQ implémenté par LINQ to DataSet et [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] convertit les données sources en collections d’objets basées sur <xref:System.Collections.IEnumerable>. Le programmeur consulte toujours les données comme une collection <xref:System.Collections.IEnumerable>, lors de l’interrogation et de la mise à jour. La prise en charge complète de `IntelliSense` est fournie pour l'écriture de requêtes sur ces collections.  
  
 Il existe trois technologies ADO.NET LINQ (Language-Integrated Query) distinctes : LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]et LINQ to Entities. LINQ to DataSet fournit une interrogation plus riche et optimisée sur le <xref:System.Data.DataSet> et [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] vous permet d’interroger directement les schémas de base de données SQL Server, et LINQ to Entities vous permet d’interroger une Entity Data Model.  
  
 Le diagramme suivant donne un aperçu de la relation des technologies ADO.NET LINQ avec les langages de programmation de haut niveau et les sources de données prenant en charge LINQ.  
  
 ![Présentation de LINQ to ADO.NET](./media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Pour plus d’informations sur LINQ, consultez [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Les sections suivantes fournissent des informations supplémentaires sur LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]et LINQ to Entities.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 Le <xref:System.Data.DataSet> est un élément clé du modèle de programmation déconnecté sur lequel ADO.NET repose et est largement utilisé. LINQ to DataSet permet aux développeurs de créer des fonctions de requête plus riches en <xref:System.Data.DataSet> à l’aide du même mécanisme de formulation de requête disponible pour de nombreuses autres sources de données. Pour plus d’informations, [consultez LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] est un outil utile pour les développeurs qui n'ont pas besoin d'effectuer de mappage à un modèle conceptuel. En utilisant [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], vous pouvez utiliser le modèle de programmation LINQ directement sur le schéma de base de données existant. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permet aux développeurs de générer des classes .NET Framework qui représentent des données. Plutôt que d'effectuer un mappage à un modèle conceptuel de données, ces classes générées effectuent un mappage direct aux tables de données, vues, procédures stockées et fonctions définies par l'utilisateur.  
  
 Avec [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], les développeurs peuvent écrire du code directement dans le schéma de stockage à l’aide du même modèle de programmation LINQ que les collections en mémoire et le <xref:System.Data.DataSet>, en plus d’autres sources de données telles que XML. Pour plus d'informations, consultez [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 La plupart des applications de gestion actuellement écrites reposent sur des bases de données relationnelles. À un certain stade, ces applications doivent interagir avec les données représentées sous forme relationnelle. Les schémas de base de données ne sont pas toujours adaptés à la création d'applications et les modèles conceptuels d'application sont différents des modèles logiques de base de données. Le Entity Data Model est un modèle de données conceptuel qui peut être utilisé pour modéliser les données d’un domaine particulier afin que les applications puissent interagir avec les données en tant qu’objets. Pour plus d’informations, consultez [ADO.NET Entity Framework](./ef/index.md).  
  
 Via l’Entity Data Model, les données relationnelles sont exposées comme objets dans l'environnement .NET. Cela fait de la couche objet une cible idéale pour la prise en charge de LINQ, permettant aux développeurs de formuler des requêtes sur la base de données à partir du langage utilisé pour générer la logique métier. Cette capacité est appelée LINQ to Entities. Pour plus d’informations, consultez [LINQ to Entities](./ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to DataSet](linq-to-dataset.md)
- [LINQ to SQL](./sql/linq/index.md)
- [LINQ to Entities](./ef/language-reference/linq-to-entities.md)
- [LINQ (Language Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
