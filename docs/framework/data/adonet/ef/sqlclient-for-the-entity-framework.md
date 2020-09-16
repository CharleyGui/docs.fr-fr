---
title: SqlClient pour Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: e9bf1014bdbc14b854d3b37d488d75878d1a3473
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552243"
---
# <a name="sqlclient-for-the-entity-framework"></a>SqlClient pour Entity Framework
Cette section décrit le fournisseur de données .NET Framework pour SQL Server (SqlClient) qui permet à Entity Framework de travailler sur Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Attribut de schéma Provider  
 `Provider` est un attribut de l'élément `Schema` en langage SSDL (Store Schema Definition Language).  
  
 Pour utiliser SqlClient, attribuez la chaîne « System.Data.SqlClient » à l'attribut `Provider` de l'élément `Schema`.  
  
## <a name="providermanifesttoken-schema-attribute"></a>Attribut de schéma ProviderManifestToken  
 `ProviderManifestToken` est un attribut obligatoire de l'élément `Schema` en SSDL. Ce jeton permet de charger le manifeste du fournisseur pour les scénarios hors connexion. Pour plus d’informations sur l' `ProviderManifestToken` attribut, consultez [Schema, élément (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).  
  
 SqlClient peut être utilisé comme fournisseur de données pour différentes versions de SQL Server. Ces versions ont des fonctionnalités différentes. Par exemple, SQL Server 2000 ne prend pas en charge `varchar(max)` les `nvarchar(max)` types et qui ont été introduits avec SQL Server 2005.  
  
 SqlClient produit et accepte les jetons du manifeste du fournisseur suivants pour les différentes versions de SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
> À compter de Visual Studio 2010, les [outils ADO.NET Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) ne prennent pas en charge SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Nom de l'espace de noms du fournisseur  
 Tous les fournisseurs doivent spécifier un espace de noms. Cette propriété indique à Entity Framework le préfixe attribué par le fournisseur à des constructions spécifiques, telles que des types et des fonctions. L'espace de noms des manifestes du fournisseur SqlClient est `SqlServer`. Pour plus d’informations sur les espaces de noms, consultez [espaces de noms](./language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Types  
 Le fournisseur SqlClient pour Entity Framework fournit des informations de mappage entre les types de modèles conceptuels et les types SQL Server. Pour plus d’informations, consultez [SqlClient pour Entity FrameworkTypes](sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Fonctions  
 Le fournisseur SqlClient pour Entity Framework définit la liste des fonctions prises en charge par le fournisseur. Pour obtenir la liste des fonctions prises en charge, consultez [SqlClient pour Entity Framework Functions](sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fonctions SqlClient pour l'Entity Framework](sqlclient-for-ef-functions.md)  
  
 [SqlClient pour Entity FrameworkTypes](sqlclient-for-ef-types.md)  
  
 [Problèmes connus dans SqlClient pour l'Entity Framework](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Voir aussi

- [Langage d'Entity SQL](./language-reference/entity-sql-language.md)
- [Référence du langage](./language-reference/index.md)
- [Problèmes connus dans le fournisseur SqlClient pour Entity Framework](sqlclient-for-the-entity-framework.md)
