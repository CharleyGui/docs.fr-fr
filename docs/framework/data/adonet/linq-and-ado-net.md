---
title: LINQ et ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: bfd5bb845917f9ca8ba3b154a51a946b610ca571
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489818"
---
# <a name="linq-and-adonet"></a>LINQ et ADO.NET
Aujourd'hui, de nombreux développeurs d’entreprise doivent utiliser des langages de programmation deux (ou plus) : un langage de haut niveau pour la logique métier vos couches présentation (tel que Visual C# ou Visual Basic) et un langage de requête pour interagir avec la base de données (par exemple, Transact-SQL) . Pour être efficace, le développeur doit être expert en plusieurs langages, et cela peut entraîner des incompatibilités dans l'environnement de développement. Par exemple, une application qui utilise une API d'accès aux données pour exécuter une requête sur une base de données spécifie la requête comme un littéral de chaîne en utilisant des guillemets. Cette chaîne de requête est illisible pour le compilateur et elle ne fait l'objet d'aucun contrôle d'erreur pour vérifier sa syntaxe ou l'existence des colonnes ou lignes auxquelles elle fait référence. Il n'y a aucune vérification de type des paramètres de requête et aucune prise en charge `IntelliSense`.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] permet aux développeurs de former des requêtes basées sur des ensembles dans leur code d'application, sans avoir à utiliser un langage de requête séparé. Vous pouvez écrire des requêtes [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sur diverses sources de données énumérables (c'est-à-dire une source de données qui implémente l'interface <xref:System.Collections.IEnumerable>), comme des structures de données en mémoire, des documents XML, des bases de données SQL et des objets <xref:System.Data.DataSet>. Bien que ces sources de données énumérables soient implémentées de diverses manières, elles exposent toutes la même syntaxe et les mêmes constructions de langage. Parce que les requêtes peuvent être formées à même le langage de programmation, vous n'avez pas à utiliser un autre langage de requêtes intégré en tant que littéraux de chaîne et qui ne peut pas être compris ou vérifié par le compilateur. Intégration des requêtes dans le langage de programmation permet également aux programmeurs de Visual Studio être plus productif en fournissant le type au moment de la compilation et la vérification de la syntaxe, et `IntelliSense`. Ces fonctionnalités réduisent la nécessité du débogage de requête et de la résolution d’erreur.  
  
 Le transfert des données à partir des tables SQL dans des objets en mémoire est souvent fastidieux et susceptible d'engendrer des erreurs. Le fournisseur [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] implémenté par [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] et [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] convertit les données sources en collections d'objets basées sur <xref:System.Collections.IEnumerable>. Le programmeur consulte toujours les données comme une collection <xref:System.Collections.IEnumerable>, lors de l'interrogation et de la mise à jour. La prise en charge complète de `IntelliSense` est fournie pour l'écriture de requêtes sur ces collections.  
  
 Il existe trois technologies ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] différentes : [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] et [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] assure une interrogation plus riche et optimisée du <xref:System.Data.DataSet> et [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] vous permet d’interroger directement des schémas de base de données SQL Server, et [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] vous permet d’interroger un [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
 Le diagramme suivant donne un aperçu de la relation des technologies ADO.NET LINQ avec les langages de programmation de haut niveau et les sources de données prenant en charge LINQ.  
  
 ![Présentation d’ADO.NET de LINQ to](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Pour plus d’informations sur LINQ, consultez [requête LINQ (Language Integrated)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Les sections ci-dessous fournissent des informations supplémentaires sur [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] et [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 Le <xref:System.Data.DataSet> est un élément clé du modèle de programmation déconnecté qui est basé sur ADO.NET et est largement utilisé. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] permet aux développeurs de générer des fonctions de requête plus complètes dans <xref:System.Data.DataSet> en utilisant les mêmes mécanismes de formulation de requêtes que de nombreuses autres sources de données. Pour plus d’informations, [consultez LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] est un outil utile pour les développeurs qui n'ont pas besoin d'effectuer de mappage à un modèle conceptuel. Avec [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], vous pouvez utiliser directement le modèle de programmation [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] un schéma de base de données existant. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permet aux développeurs de générer des classes .NET Framework qui représentent les données. Plutôt que d'effectuer un mappage à un modèle conceptuel de données, ces classes générées effectuent un mappage direct aux tables de données, vues, procédures stockées et fonctions définies par l'utilisateur.  
  
 Avec [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], les développeurs peuvent écrire directement du code par rapport au modèle de stockage en utilisant le même modèle de programmation [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] que dans les collections en mémoire et le <xref:System.Data.DataSet>, en plus d'autres sources de données telles que XML. Pour plus d’informations, consultez [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 La plupart des applications de gestion actuellement écrites reposent sur des bases de données relationnelles. À un certain stade, ces applications doivent interagir avec les données représentées sous forme relationnelle. Les schémas de base de données ne sont pas toujours adaptés à la création d'applications et les modèles conceptuels d'application sont différents des modèles logiques de base de données. Le [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] est un modèle conceptuel de données pouvant être utilisé pour modéliser les données d'un domaine particulier de sorte que des applications interagissent avec les données comme des objets. Consultez [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) pour plus d’informations.  
  
 Via le [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], les données relationnelles sont exposées comme objets dans l'environnement .NET. Cela fait de la couche objet une cible idéale pour la prise en charge [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], permettant aux développeurs de formuler des requêtes sur la base de données à partir du langage utilisé pour générer la logique métier. Cette capacité porte le nom de [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. Pour plus d’informations, consultez [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [LINQ (Language Integrated Query)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
