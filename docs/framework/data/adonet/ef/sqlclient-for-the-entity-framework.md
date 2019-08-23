---
title: SqlClient pour Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: ec67637c416f2560c1f5d0a9fd0e856703820a84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954967"
---
# <a name="sqlclient-for-the-entity-framework"></a>SqlClient pour Entity Framework
Cette section décrit le fournisseur de données .NET Framework pour SQL Server (SqlClient) qui permet à Entity Framework de travailler sur Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Attribut de schéma Provider  
 `Provider` est un attribut de l'élément `Schema` en langage SSDL (Store Schema Definition Language).  
  
 Pour utiliser SqlClient, attribuez la chaîne « System.Data.SqlClient » à l'attribut `Provider` de l'élément `Schema`.  
  
## <a name="providermanifesttoken-schema-attribute"></a>Attribut de schéma ProviderManifestToken  
 `ProviderManifestToken` est un attribut obligatoire de l'élément `Schema` en SSDL. Ce jeton permet de charger le manifeste du fournisseur pour les scénarios hors connexion. Pour plus d’informations `ProviderManifestToken` sur l’attribut, consultez [Schema, élément (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).  
  
 SqlClient peut être utilisé comme fournisseur de données pour différentes versions de SQL Server. Ces versions ont des fonctionnalités différentes. Par exemple, SQL Server 2000 ne prend pas `varchar(max)` en `nvarchar(max)` charge les types et qui ont été introduits avec SQL Server 2005.  
  
 SqlClient produit et accepte les jetons du manifeste du fournisseur suivants pour les différentes versions de SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
> À compter de Visual Studio 2010, les [outils ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) ne prennent pas en charge SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Nom de l'espace de noms du fournisseur  
 Tous les fournisseurs doivent spécifier un espace de noms. Cette propriété indique à Entity Framework le préfixe attribué par le fournisseur à des constructions spécifiques, telles que des types et des fonctions. L'espace de noms des manifestes du fournisseur SqlClient est `SqlServer`. Pour plus d’informations sur les espaces de noms, consultez [espaces de noms](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Types  
 Le fournisseur SqlClient pour Entity Framework fournit des informations de mappage entre les types de modèles conceptuels et les types SQL Server. Pour plus d’informations, consultez [SqlClient pour Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Fonctions  
 Le fournisseur SqlClient pour Entity Framework définit la liste des fonctions prises en charge par le fournisseur. Pour obtenir la liste des fonctions prises en charge, consultez [SqlClient pour Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fonctions SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [SqlClient pour Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Problèmes connus dans SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Voir aussi

- [Langage Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Informations de référence sur le langage](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [Problèmes connus dans le fournisseur SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
