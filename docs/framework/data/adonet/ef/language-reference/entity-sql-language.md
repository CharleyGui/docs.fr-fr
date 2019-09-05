---
title: Langage d'Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251015"
---
# <a name="entity-sql-language"></a>Langage d'Entity SQL
Entity SQL est un langage de requête indépendant du stockage et semblable à SQL. Entity SQL vous permet d'interroger des données d'entité, en tant qu'objets ou sous une forme tabulaire. Vous devez envisager d'utiliser Entity SQL dans les cas suivants :  
  
- Lorsqu'une requête doit être construite dynamiquement au moment de l'exécution. Dans ce cas, vous devez également envisager d'utiliser les méthodes du Générateur de requêtes d'<xref:System.Data.Objects.ObjectQuery%601> au lieu de construire une chaîne de requête Entity SQL au moment de l'exécution.  
  
- Lorsque vous voulez définir une requête dans le cadre de la définition du modèle. Seul Entity SQL est pris en charge dans un modèle de données. Pour plus d’informations, consultez [QueryView, élément (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl) .  
  
- Lorsque vous utilisez EntityClient pour retourner des données d'entité en lecture seule sous la forme d'ensembles de lignes à l'aide d'un <xref:System.Data.EntityClient.EntityDataReader>. Pour plus d’informations, consultez [fournisseur EntityClient pour le Entity Framework](../entityclient-provider-for-the-entity-framework.md).  
  
- Si vous êtes déjà un expert des langages de requête basés sur SQL, Entity SQL peut vous sembler le choix le plus naturel.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Utilisation de Entity SQL avec le fournisseur EntityClient  
 Pour plus d'informations sur l'utilisation de Entity SQL avec le fournisseur EntityClient, consultez les rubriques suivantes :  
  
 [Fournisseur EntityClient pour Entity Framework](../entityclient-provider-for-the-entity-framework.md)  
  
 [Guide pratique pour Créer une chaîne de connexion EntityConnection](../how-to-build-an-entityconnection-connection-string.md)  
  
 [Guide pratique pour Exécuter une requête qui retourne les résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Guide pratique pour Exécuter une requête qui retourne les résultats StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Guide pratique pour Exécuter une requête qui retourne les résultats RefType](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Guide pratique pour Exécuter une requête qui retourne des types complexes](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Guide pratique : Exécuter une requête qui retourne des collections imbriquées](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Guide pratique : Exécuter une requête Entity SQL paramétrable à l’aide d’EntityCommand](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Guide pratique pour Exécuter une procédure stockée paramétrable à l’aide d’EntityCommand](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Guide pratique pour Exécuter une requête polymorphe](../how-to-execute-a-polymorphic-query.md)  
  
 [Guide pratique pour Parcourir les relations avec l’opérateur Navigate](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Utilisation de Entity SQL avec des requêtes d'objet  
 Pour plus d'informations sur l'utilisation de Entity SQL avec des requêtes d'objet, consultez les rubriques suivantes :  
  
 [Guide pratique pour Exécuter une requête qui retourne des objets de type d’entité](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Guide pratique pour Exécuter une requête paramétrable](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Guide pratique : Parcourir les relations à l’aide des propriétés de navigation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Guide pratique pour Appeler une fonction définie par l’utilisateur](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Guide pratique pour Filtrer les données](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Guide pratique pour Trier les données](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Guide pratique : Grouper les données](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Guide pratique : Agréger des données](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Guide pratique pour Exécuter une requête qui retourne des objets de type anonyme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Guide pratique : Exécuter une requête qui retourne une collection de types primitifs](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Guide pratique : Interroger des objets liés dans un EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Guide pratique pour Ordonner l’Union de deux requêtes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Guide pratique pour Page des résultats de la requête](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)  
  
 [Référence Entity SQL](entity-sql-reference.md)  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](../index.md)
- [Informations de référence sur le langage](index.md)
