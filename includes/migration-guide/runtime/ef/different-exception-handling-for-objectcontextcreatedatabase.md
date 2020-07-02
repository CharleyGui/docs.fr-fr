---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620015"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Gestion des exceptions différente pour les méthodes ObjectContext.CreateDatabase et DbProviderServices.CreateDatabase

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, en cas d’échec de la création d’une base de données, les méthodes <code>CreateDatabase</code> tentent de supprimer la base de données vide. Si cette opération réussit, l’exception <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> d’origine est propagée (au lieu de l’exception <xref:System.InvalidOperationException?displayProperty=fullName> qui était systématiquement levée dans .NET Framework 4.0).

#### <a name="suggestion"></a>Suggestion

Quand vous interceptez une <xref:System.InvalidOperationException?displayProperty=fullName> en exécutant <xref:System.Data.Objects.ObjectContext.CreateDatabase> ou <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions doit maintenant également être interceptée.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
