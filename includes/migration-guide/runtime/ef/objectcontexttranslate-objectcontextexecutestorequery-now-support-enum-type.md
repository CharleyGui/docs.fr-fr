---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620028"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate et ObjectContext.ExecuteStoreQuery prennent maintenant en charge le type enum

#### <a name="details"></a>Détails

Dans .NET Framework 4.0, le paramètre générique <code>T</code> des méthodes <code>ObjectContext.Translate</code> et <code>ObjectContext.ExecuteStoreQuery</code> ne pouvait pas être une énumération. Ce scénario est désormais pris en charge.

#### <a name="suggestion"></a>Suggestion

Si Translate ou ExecuteStoreQuery était appelé sur un type enum dans .NET Framework 4.0, la valeur « 0 » était retournée. Si ce comportement était celui souhaité, les appels devaient être remplacés par une constante 0 (ou l’équivalent enum de celle-ci).

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
