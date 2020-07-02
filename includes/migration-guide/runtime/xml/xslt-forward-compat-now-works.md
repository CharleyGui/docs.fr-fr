---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620515"
---
### <a name="xslt-forward-compat-now-works"></a>La compatibilité ascendante de XSLT fonctionne désormais

#### <a name="details"></a>Détails

Dans .NET Framework 4, la compatibilité ascendante de XSLT 1.0 avait les problèmes suivants :<ul><li>Le chargement d'une feuille de style échouait si sa version avait la valeur 2.0 et si l'analyseur rencontrait une construction XSLT 1.0 non reconnue.</li><li>La construction <code>xsl:sort</code> ne pouvait pas trier les données si la version de la feuille de style était définie sur 1.1.</li></ul>Dans le .NET Framework 4.5, ces problèmes ont été résolus et le mode de compatibilité ascendante de XSLT 1.0 fonctionne correctement.

#### <a name="suggestion"></a>Suggestion

La plupart des applications ne devraient pas être affectées, mais les données sont triées différemment dans certains cas maintenant que xsl:sort est respecté. Si <code>xsl:sort</code> est utilisé dans des feuilles de style 1.1, vérifiez que les applications ne dépendaient pas de l’ordre non trié des données. Si des applications s’appuient sur le comportement de tri de la version 4.0, supprimez <code>xsl:sort</code> de la feuille de style.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
