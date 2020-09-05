---
ms.openlocfilehash: 8c593fa6490451c6236f0d4390f09d4e9e4f0cbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497008"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="06fd9-101">Gestion des exceptions différente pour les méthodes ObjectContext.CreateDatabase et DbProviderServices.CreateDatabase</span><span class="sxs-lookup"><span data-stu-id="06fd9-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

#### <a name="details"></a><span data-ttu-id="06fd9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="06fd9-102">Details</span></span>

<span data-ttu-id="06fd9-103">À compter de .NET Framework 4.5, en cas d’échec de la création d’une base de données, les méthodes <code>CreateDatabase</code> tentent de supprimer la base de données vide.</span><span class="sxs-lookup"><span data-stu-id="06fd9-103">Beginning in .NET Framework 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="06fd9-104">Si cette opération réussit, l’exception <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> d’origine est propagée (au lieu de l’exception <xref:System.InvalidOperationException?displayProperty=fullName> qui était systématiquement levée dans .NET Framework 4.0).</span><span class="sxs-lookup"><span data-stu-id="06fd9-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=fullName> that was always thrown in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="06fd9-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="06fd9-105">Suggestion</span></span>

<span data-ttu-id="06fd9-106">Quand vous interceptez une <xref:System.InvalidOperationException?displayProperty=fullName> en exécutant <xref:System.Data.Objects.ObjectContext.CreateDatabase> ou <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions doit maintenant également être interceptée.</span><span class="sxs-lookup"><span data-stu-id="06fd9-106">When catching an <xref:System.InvalidOperationException?displayProperty=fullName> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>

| <span data-ttu-id="06fd9-107">Name</span><span class="sxs-lookup"><span data-stu-id="06fd9-107">Name</span></span>    | <span data-ttu-id="06fd9-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="06fd9-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="06fd9-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="06fd9-109">Scope</span></span>   |<span data-ttu-id="06fd9-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="06fd9-110">Minor</span></span>|
|<span data-ttu-id="06fd9-111">Version</span><span class="sxs-lookup"><span data-stu-id="06fd9-111">Version</span></span>|<span data-ttu-id="06fd9-112">4,5</span><span class="sxs-lookup"><span data-stu-id="06fd9-112">4.5</span></span>|
|<span data-ttu-id="06fd9-113">Type</span><span class="sxs-lookup"><span data-stu-id="06fd9-113">Type</span></span>|<span data-ttu-id="06fd9-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="06fd9-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="06fd9-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="06fd9-115">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>
- <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`
- `M:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)`

-->
