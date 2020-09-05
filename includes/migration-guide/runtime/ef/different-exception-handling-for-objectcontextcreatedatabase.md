---
ms.openlocfilehash: 8c593fa6490451c6236f0d4390f09d4e9e4f0cbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497008"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Gestion des exceptions différente pour les méthodes ObjectContext.CreateDatabase et DbProviderServices.CreateDatabase

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, en cas d’échec de la création d’une base de données, les méthodes <code>CreateDatabase</code> tentent de supprimer la base de données vide. Si cette opération réussit, l’exception <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> d’origine est propagée (au lieu de l’exception <xref:System.InvalidOperationException?displayProperty=fullName> qui était systématiquement levée dans .NET Framework 4.0).

#### <a name="suggestion"></a>Suggestion

Quand vous interceptez une <xref:System.InvalidOperationException?displayProperty=fullName> en exécutant <xref:System.Data.Objects.ObjectContext.CreateDatabase> ou <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions doit maintenant également être interceptée.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>
- <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`
- `M:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)`

-->
