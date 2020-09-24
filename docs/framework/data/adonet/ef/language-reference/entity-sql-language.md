---
title: Langage d'Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 721a4cd9d4e5618c083392bbe1ae203f285f8feb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148112"
---
# <a name="entity-sql-language"></a>Langage d'Entity SQL

Entity SQL est un langage de requête indépendant du stockage et semblable à SQL. Entity SQL vous permet d'interroger des données d'entité, en tant qu'objets ou sous une forme tabulaire. Vous devez envisager d'utiliser Entity SQL dans les cas suivants :  
  
- Lorsqu'une requête doit être construite dynamiquement au moment de l'exécution. Dans ce cas, vous devez également envisager d'utiliser les méthodes du Générateur de requêtes d'<xref:System.Data.Objects.ObjectQuery%601> au lieu de construire une chaîne de requête Entity SQL au moment de l'exécution.  
  
- Lorsque vous voulez définir une requête dans le cadre de la définition du modèle. Seul Entity SQL est pris en charge dans un modèle de données. Pour plus d’informations, consultez [QueryView, élément (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl) .  
  
- Lorsque vous utilisez EntityClient pour retourner des données d'entité en lecture seule sous la forme d'ensembles de lignes à l'aide d'un <xref:System.Data.EntityClient.EntityDataReader>. Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](../entityclient-provider-for-the-entity-framework.md).  
  
- Si vous êtes déjà un expert des langages de requête basés sur SQL, Entity SQL peut vous sembler le choix le plus naturel.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Utilisation de Entity SQL avec le fournisseur EntityClient  

 Pour plus d'informations sur l'utilisation de Entity SQL avec le fournisseur EntityClient, consultez les rubriques suivantes :  
  
 [Fournisseur EntityClient pour Entity Framework](../entityclient-provider-for-the-entity-framework.md)  
  
 [Procédure : Créer une chaîne de connexion EntityConnection](../how-to-build-an-entityconnection-connection-string.md)  
  
 [Procédure : Exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Procédure : Exécuter une requête qui retourne des résultats StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Procédure : Exécuter une requête qui retourne des résultats RefType](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Procédure : Exécuter une requête qui retourne des types complexes](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Procédure : Exécuter une requête qui retourne des collections imbriquées](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Procédure : Exécuter une requête paramétrable Entity SQL avec EntityCommand](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Procédure : Exécuter une procédure stockée paramétrable avec EntityCommand](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Procédure : Exécuter une requête polymorphe](../how-to-execute-a-polymorphic-query.md)  
  
 [Procédure : Parcourir les relations avec l’opérateur Navigate](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Utilisation de Entity SQL avec des requêtes d'objet  

 Pour plus d'informations sur l'utilisation de Entity SQL avec des requêtes d'objet, consultez les rubriques suivantes :  
  
 [Comment : exécuter une requête qui retourne les objets de type entity](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Comment : exécuter une requête paramétrée](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Comment : parcourir les relations à l'aide des propriétés de navigation](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Comment : appeler une fonction définie par l'utilisateur](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Comment : filtrer les données](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Comment : trier les données](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Comment : grouper les données](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Comment : agréger des données](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Comment : exécuter une requête qui retourne des objets de type anonyme](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Comment : exécuter une requête qui retourne une collection de types primitifs](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Comment : interroger des objets liés dans une EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Comment : ordonner l'union de deux requêtes](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Procédure : pagination dans les résultats d’une requête](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>Dans cette section  

 [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)  
  
 [Référence Entity SQL](entity-sql-reference.md)  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](../index.md)
- [Informations de référence sur le langage](index.md)
