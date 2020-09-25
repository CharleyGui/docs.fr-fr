---
title: Fournisseur EntityClient pour Entity Framework
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 9b3194e4a85eda6f405a3ab85723ac2cb9d00090
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181074"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Fournisseur EntityClient pour Entity Framework

Le fournisseur EntityClient est un fournisseur de données utilisé par les applications Entity Framework pour accéder à des données décrites dans un modèle conceptuel. Pour plus d’informations sur les modèles conceptuels, consultez [modélisation et mappage](modeling-and-mapping.md). EntityClient utilise d'autres fournisseurs de données .NET Framework pour accéder à la source de données. Par exemple, EntityClient utilise le fournisseur de données .NET Framework pour SQL Server (SqlClient) lors de l'accès à une base de données SQL Server. Pour plus d’informations sur le fournisseur SqlClient, consultez [SqlClient pour le Entity Framework](sqlclient-for-the-entity-framework.md). Le fournisseur EntityClient est implémenté dans l'espace de noms <xref:System.Data.EntityClient>.  
  
## <a name="managing-connections"></a>Gestion des connexions  

 Le Entity Framework s’appuie sur des fournisseurs de données ADO.NET spécifiques au stockage en fournissant un <xref:System.Data.EntityClient.EntityConnection> à un fournisseur de données sous-jacent et à une base de données relationnelle. Pour construire un <xref:System.Data.EntityClient.EntityConnection> objet, vous devez référencer un ensemble de métadonnées qui contient les modèles et le mappage nécessaires, ainsi qu’un nom de fournisseur de données spécifique au stockage et une chaîne de connexion. Une fois le <xref:System.Data.EntityClient.EntityConnection> est en place, les entités sont accessibles via les classes générées à partir du modèle conceptuel.  
  
 Vous pouvez spécifier une chaîne de connexion dans le fichier app.config.  
  
 <xref:System.Data.EntityClient> comprend également la classe <xref:System.Data.EntityClient.EntityConnectionStringBuilder>. Cette classe permet aux développeurs de créer par programme des chaînes de connexion correctes du point de vue syntaxique, et d'analyser et régénérer les chaînes de connexion existantes, à l'aide des propriétés et des méthodes de la classe. Pour plus d’informations, consultez [Comment : générer une chaîne de connexion EntityConnection](how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Création de requêtes  

 Le [!INCLUDE[esql](../../../../../includes/esql-md.md)] langage est un dialecte SQL indépendant du stockage qui fonctionne directement avec les schémas d’entité conceptuels et prend en charge Entity Data Model concepts tels que l’héritage et les relations. La <xref:System.Data.EntityClient.EntityCommand> classe est utilisée pour exécuter une [!INCLUDE[esql](../../../../../includes/esql-md.md)] commande sur un modèle d’entité. Au moment de la construction d'objets <xref:System.Data.EntityClient.EntityCommand>, vous pouvez spécifier un nom de procédure stockée ou un texte de requête. Le Entity Framework fonctionne avec les fournisseurs de données spécifiques au stockage pour traduire le générique [!INCLUDE[esql](../../../../../includes/esql-md.md)] en requêtes spécifiques au stockage. Pour plus d’informations sur l’écriture de [!INCLUDE[esql](../../../../../includes/esql-md.md)] requêtes, consultez [Entity SQL Language](./language-reference/entity-sql-language.md).  
  
 L’exemple suivant crée un <xref:System.Data.EntityClient.EntityCommand> objet et assigne un [!INCLUDE[esql](../../../../../includes/esql-md.md)] texte de requête à sa <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> propriété. Cette [!INCLUDE[esql](../../../../../includes/esql-md.md)] requête demande les produits classés selon le tarif du modèle conceptuel. Le code suivant fait une totale abstraction du modèle de stockage.  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>Exécution de requêtes  

 Lorsqu’une requête est exécutée, elle est analysée et convertie en arborescence de commandes canonique. Tous les traitements ultérieurs sont exécutés sur l'arborescence de commandes. L’arborescence de commandes est le moyen de communication entre <xref:System.Data.EntityClient> et le fournisseur de données .NET Framework sous-jacent, tel que <xref:System.Data.SqlClient> .  
  
 <xref:System.Data.EntityClient.EntityDataReader> expose les résultats de l'exécution d'un objet <xref:System.Data.EntityClient.EntityCommand> sur un modèle conceptuel. Pour exécuter la commande qui retourne l'objet <xref:System.Data.EntityClient.EntityDataReader>, appelez la méthode <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> implémente <xref:System.Data.IExtendedDataRecord> pour décrire des résultats structurés et enrichis.  
  
## <a name="managing-transactions"></a>Gestion des transactions  

 Dans Entity Framework, il existe deux modes d’utilisation des transactions : automatique et explicite. Les transactions automatiques utilisent l'espace de noms <xref:System.Transactions>, tandis que les transactions explicites utilisent la classe <xref:System.Data.EntityClient.EntityTransaction>.  
  
 Pour mettre à jour des données exposées via un modèle conceptuel, consultez [How to : Manage transactions in the Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100)).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Procédure : Créer une chaîne de connexion EntityConnection](how-to-build-an-entityconnection-connection-string.md)  
  
 [Procédure : Exécuter une requête qui retourne des résultats PrimitiveType](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Procédure : Exécuter une requête qui retourne des résultats StructuralType](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Procédure : Exécuter une requête qui retourne des résultats RefType](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Procédure : Exécuter une requête qui retourne des types complexes](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Procédure : Exécuter une requête qui retourne des collections imbriquées](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Procédure : Exécuter une requête paramétrable Entity SQL avec EntityCommand](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Procédure : Exécuter une procédure stockée paramétrable avec EntityCommand](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Procédure : Exécuter une requête polymorphe](how-to-execute-a-polymorphic-query.md)  
  
 [Procédure : Parcourir les relations avec l’opérateur Navigate](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Voir aussi

- [Gestion des connexions et des transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](index.md)
- [Informations de référence sur le langage](./language-reference/index.md)
