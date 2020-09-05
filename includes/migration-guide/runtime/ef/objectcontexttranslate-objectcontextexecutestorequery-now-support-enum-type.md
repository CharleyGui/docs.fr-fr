---
ms.openlocfilehash: 81992e57d7e92b4df92ce68870c0272d6cd5b220
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496423"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate et ObjectContext.ExecuteStoreQuery prennent maintenant en charge le type enum

#### <a name="details"></a>Détails

Dans .NET Framework 4.0, le paramètre générique <code>T</code> des méthodes <code>ObjectContext.Translate</code> et <code>ObjectContext.ExecuteStoreQuery</code> ne pouvait pas être une énumération. Ce scénario est désormais pris en charge.

#### <a name="suggestion"></a>Suggestion

Si Translate ou ExecuteStoreQuery était appelé sur un type enum dans .NET Framework 4.0, la valeur « 0 » était retournée. Si ce comportement était celui souhaité, les appels devaient être remplacés par une constante 0 (ou l’équivalent enum de celle-ci).

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

<!--

#### Affected APIs

- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader)``
- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.Object[])``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])``

-->
