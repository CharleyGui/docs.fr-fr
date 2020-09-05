---
ms.openlocfilehash: 6a79f04af44f78313c4d5bb5c37dfad252d3024b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497030"
---
### <a name="product-versioning-changes-in-the-net-framework-46-and-later-versions"></a>Modifications de la gestion de versions de produit dans .NET Framework 4.6 et versions ultérieures

#### <a name="details"></a>Détails

La gestion des versions de produit a changé depuis les mises en production précédentes du .NET Framework, notamment par rapport à .NET Framework 4, 4.5, 4.5.1 et 4.5.2. Voici le détail des modifications :<ul><li>La valeur de l’entrée <code>Version</code> dans la clé <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> a été remplacée par <code>4.6.xxxxx</code> pour .NET Framework 4.6 et ses versions intermédiaires, et par <code>4.7.xxxxx</code> pour .NET Framework 4.7 et 4.7.1. Dans .NET Framework 4.5, 4.5.1 et 4.5.2, elle était au format <code>4.5.xxxxx</code>.</li><li>La gestion de versions de produit et de fichier pour les fichiers du .NET Framework est passée de l’ancien schéma 4.0.30319.x au schéma 4.6.X.0 pour .NET Framework 4.6 et ses versions intermédiaires, et au schéma 4.7.X.0 pour .NET Framework 4.7 et 4.7.1. Pour voir ces nouvelles valeurs, cliquez avec le bouton droit sur un fichier, puis affichez ses propriétés.</li><li>Les attributs <xref:System.Reflection.AssemblyFileVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute> pour les assemblys managés ont des valeurs Version au format 4.6.X.0 pour .NET Framework 4.6 et ses versions intermédiaires, et 4.7.X.0 pour .NET Framework 4.7 et 4.7.1.</li><li>Dans .NET Framework 4.6, 4.6.1, 4.6.2, 4.7 et 4.7.1, la propriété <xref:System.Environment.Version?displayProperty=nameWithType> retourne la chaîne de version fixe <code>4.0.30319.42000</code>. Dans .NET Framework 4, 4.5, 4.5.1 et 4.5.2, elle retourne les chaînes de version au format <code>4.0.30319.xxxxx</code> (par exemple, &quot;4.0.30319.18010&quot;). Notez que nous ne recommandons pas que le code d’application prenne de nouvelles dépendances sur la propriété Environment.Version.</li></ul>Pour plus d’informations, consultez [Guide pratique pour déterminer les versions du .NET Framework installées](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

#### <a name="suggestion"></a>Suggestion

En général, les applications doivent s'appuyer sur les techniques recommandées pour la détection d'éléments tels que la version de runtime du .NET Framework et le répertoire d'installation :<ul><li>Pour détecter la version de runtime du .NET Framework, consultez [Guide pratique pour déterminer les versions .NET Framework installées](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</li><li>Pour déterminer le chemin d'installation du .NET Framework, utilisez la valeur de l'entrée <code>InstallPath</code> dans la clé <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code>.</li></ul> <blockquote> [!IMPORTANT] Le nom de la sous-clé est <code>NET Framework Setup</code>, et non <code>.NET Framework Setup</code>.</blockquote> <ul><li>Pour déterminer le chemin d'accès du répertoire du Common Language Runtime du .NET Framework, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory?displayProperty=nameWithType>.</li><li>Pour obtenir la version du CLR, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion?displayProperty=nameWithType>. Pour .NET Framework 4 et ses versions intermédiaires (.NET Framework 4.5, 4.5.1, 4.5.2 ainsi que .NET Framework 4.6, 4.6.1, 4.6.2, 4.7 et 4.7.1), elle retourne la chaîne v4.0.30319.</li></ul>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,6|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
