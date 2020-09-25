---
title: Espaces de noms (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7a53f8e7e70dbc9fa505f7f8619af10a0e44c331
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197805"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="f8100-102">Espaces de noms (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f8100-102">Namespaces (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f8100-103">introduit les espaces de noms afin d'éviter les conflits de noms des identificateurs globaux tels que les noms de types, les jeux d'entités, les fonctions, etc.</span><span class="sxs-lookup"><span data-stu-id="f8100-103">introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="f8100-104">La prise en charge de l’espace de noms dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est similaire à la prise en charge des espaces de noms dans la .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8100-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f8100-105">fournit deux formes de la clause USING : les espaces de noms qualifiés (où un alias plus court est fourni pour l'espace de noms) et les espaces de noms non qualifiés, tels qu'illustrés dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f8100-105">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="f8100-106">Règles de résolution de noms</span><span class="sxs-lookup"><span data-stu-id="f8100-106">Name Resolution Rules</span></span>  

 <span data-ttu-id="f8100-107">Si un identificateur ne peut pas être résolu dans les portées locales, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente de localiser le nom dans les portées globales (les espaces de noms).</span><span class="sxs-lookup"><span data-stu-id="f8100-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f8100-108">tente tout d'abord de faire correspondre l'identificateur (préfixe) avec l'un des espaces de noms qualifiés.</span><span class="sxs-lookup"><span data-stu-id="f8100-108">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="f8100-109">En cas de correspondance, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente de résoudre le reste de l’identificateur dans l’espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="f8100-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="f8100-110">Si aucune correspondance n'est trouvée, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="f8100-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="f8100-111">Tente ensuite [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de Rechercher l’identificateur dans tous les espaces de noms non qualifiés (spécifiés dans le prologue).</span><span class="sxs-lookup"><span data-stu-id="f8100-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="f8100-112">Si l'identificateur est localisé dans exactement un espace de noms, cet emplacement est retourné.</span><span class="sxs-lookup"><span data-stu-id="f8100-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="f8100-113">Si plusieurs espaces de noms ont une correspondance pour cet identificateur, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="f8100-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="f8100-114">Si aucun espace de noms ne peut être identifié pour l’identificateur, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passe le nom à l’étendue externe suivante (l' <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbConnection> objet ou), comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f8100-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="f8100-115">Différences par rapport au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f8100-115">Differences from the .NET Framework</span></span>  

 <span data-ttu-id="f8100-116">Dans le .NET Framework, vous pouvez utiliser des espaces de noms partiellement qualifiés.</span><span class="sxs-lookup"><span data-stu-id="f8100-116">In the .NET Framework, you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f8100-117">ne permet pas cela.</span><span class="sxs-lookup"><span data-stu-id="f8100-117">does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="f8100-118">Utilisation d'ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f8100-118">ADO.NET Usage</span></span>  

 <span data-ttu-id="f8100-119">Les requêtes sont exprimées par le biais d'objets <xref:System.Data.Common.DbCommand> ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f8100-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="f8100-120">Les objets <xref:System.Data.Common.DbCommand> peuvent être créés à partir d'objets <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="f8100-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="f8100-121">Il est également possible de spécifier des espaces de noms comme faisant partie des objets <xref:System.Data.Common.DbCommand> et <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="f8100-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="f8100-122">Si [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne peut pas résoudre un identificateur dans la requête elle-même, les espaces de noms externes sont détectés (selon des règles similaires).</span><span class="sxs-lookup"><span data-stu-id="f8100-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8100-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8100-123">See also</span></span>

- [<span data-ttu-id="f8100-124">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8100-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f8100-125">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f8100-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
