---
title: SqlClient pour Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 7f3a1d4bbd18977bbb1dc9ce65140428ea6fe2f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156535"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="35611-102">SqlClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="35611-102">SqlClient for the Entity Framework</span></span>

<span data-ttu-id="35611-103">Cette section décrit le fournisseur de données .NET Framework pour SQL Server (SqlClient) qui permet à Entity Framework de travailler sur Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="35611-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="35611-104">Attribut de schéma Provider</span><span class="sxs-lookup"><span data-stu-id="35611-104">Provider Schema Attribute</span></span>  

 <span data-ttu-id="35611-105">`Provider` est un attribut de l'élément `Schema` en langage SSDL (Store Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="35611-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="35611-106">Pour utiliser SqlClient, attribuez la chaîne « System.Data.SqlClient » à l'attribut `Provider` de l'élément `Schema`.</span><span class="sxs-lookup"><span data-stu-id="35611-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="35611-107">Attribut de schéma ProviderManifestToken</span><span class="sxs-lookup"><span data-stu-id="35611-107">ProviderManifestToken Schema Attribute</span></span>  

 <span data-ttu-id="35611-108">`ProviderManifestToken` est un attribut obligatoire de l'élément `Schema` en SSDL.</span><span class="sxs-lookup"><span data-stu-id="35611-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="35611-109">Ce jeton permet de charger le manifeste du fournisseur pour les scénarios hors connexion.</span><span class="sxs-lookup"><span data-stu-id="35611-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="35611-110">Pour plus d’informations sur l' `ProviderManifestToken` attribut, consultez [Schema, élément (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="35611-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="35611-111">SqlClient peut être utilisé comme fournisseur de données pour différentes versions de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="35611-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="35611-112">Ces versions ont des fonctionnalités différentes.</span><span class="sxs-lookup"><span data-stu-id="35611-112">These versions have different capabilities.</span></span> <span data-ttu-id="35611-113">Par exemple, SQL Server 2000 ne prend pas en charge `varchar(max)` les `nvarchar(max)` types et qui ont été introduits avec SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="35611-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="35611-114">SqlClient produit et accepte les jetons du manifeste du fournisseur suivants pour les différentes versions de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="35611-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="35611-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="35611-115">SQL Server 2000</span></span>|<span data-ttu-id="35611-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="35611-116">SQL Server 2005</span></span>|<span data-ttu-id="35611-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="35611-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="35611-118">2000</span><span class="sxs-lookup"><span data-stu-id="35611-118">2000</span></span>|<span data-ttu-id="35611-119">2005</span><span class="sxs-lookup"><span data-stu-id="35611-119">2005</span></span>|<span data-ttu-id="35611-120">2008</span><span class="sxs-lookup"><span data-stu-id="35611-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="35611-121">À compter de Visual Studio 2010, les [outils ADO.NET Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) ne prennent pas en charge SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="35611-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="35611-122">Nom de l'espace de noms du fournisseur</span><span class="sxs-lookup"><span data-stu-id="35611-122">Provider Namespace Name</span></span>  

 <span data-ttu-id="35611-123">Tous les fournisseurs doivent spécifier un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="35611-123">All providers must specify a namespace.</span></span> <span data-ttu-id="35611-124">Cette propriété indique à Entity Framework le préfixe attribué par le fournisseur à des constructions spécifiques, telles que des types et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="35611-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="35611-125">L'espace de noms des manifestes du fournisseur SqlClient est `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="35611-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="35611-126">Pour plus d’informations sur les espaces de noms, consultez [espaces de noms](./language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="35611-126">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="35611-127">Types</span><span class="sxs-lookup"><span data-stu-id="35611-127">Types</span></span>  

 <span data-ttu-id="35611-128">Le fournisseur SqlClient pour Entity Framework fournit des informations de mappage entre les types de modèles conceptuels et les types SQL Server.</span><span class="sxs-lookup"><span data-stu-id="35611-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="35611-129">Pour plus d’informations, consultez [SqlClient pour Entity FrameworkTypes](sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="35611-129">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="35611-130">Fonctions</span><span class="sxs-lookup"><span data-stu-id="35611-130">Functions</span></span>  

 <span data-ttu-id="35611-131">Le fournisseur SqlClient pour Entity Framework définit la liste des fonctions prises en charge par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="35611-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="35611-132">Pour obtenir la liste des fonctions prises en charge, consultez [SqlClient pour Entity Framework Functions](sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="35611-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35611-133">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="35611-133">In This Section</span></span>  

 [<span data-ttu-id="35611-134">Fonctions SqlClient pour l'Entity Framework</span><span class="sxs-lookup"><span data-stu-id="35611-134">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="35611-135">SqlClient pour Entity FrameworkTypes</span><span class="sxs-lookup"><span data-stu-id="35611-135">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="35611-136">Problèmes connus dans SqlClient pour l'Entity Framework</span><span class="sxs-lookup"><span data-stu-id="35611-136">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="35611-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35611-137">See also</span></span>

- [<span data-ttu-id="35611-138">Langage d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="35611-138">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="35611-139">Référence du langage</span><span class="sxs-lookup"><span data-stu-id="35611-139">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="35611-140">Problèmes connus dans le fournisseur SqlClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="35611-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
