---
ms.openlocfilehash: 8c8477ae3719cfcc2060459ba85bcc9e76f11c41
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497769"
---
### <a name="xslt-forward-compat-now-works"></a>La compatibilité ascendante de XSLT fonctionne désormais

#### <a name="details"></a>Détails

Dans .NET Framework 4, la compatibilité ascendante de XSLT 1.0 avait les problèmes suivants :<ul><li>Le chargement d'une feuille de style échouait si sa version avait la valeur 2.0 et si l'analyseur rencontrait une construction XSLT 1.0 non reconnue.</li><li>La construction <code>xsl:sort</code> ne pouvait pas trier les données si la version de la feuille de style était définie sur 1.1.</li></ul>Dans le .NET Framework 4.5, ces problèmes ont été résolus et le mode de compatibilité ascendante de XSLT 1.0 fonctionne correctement.

#### <a name="suggestion"></a>Suggestion

La plupart des applications ne devraient pas être affectées, mais les données sont triées différemment dans certains cas maintenant que xsl:sort est respecté. Si <code>xsl:sort</code> est utilisé dans des feuilles de style 1.1, vérifiez que les applications ne dépendaient pas de l’ordre non trié des données. Si des applications s’appuient sur le comportement de tri de la version 4.0, supprimez <code>xsl:sort</code> de la feuille de style.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Xml.Xsl.XslCompiledTransform`

-->
