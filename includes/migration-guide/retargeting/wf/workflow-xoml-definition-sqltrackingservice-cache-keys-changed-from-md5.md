---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "72846987"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>La définition XOML du workflow et les clés de cache SqlTrackingService sont passées de MD5 à SHA256

|   |   |
|---|---|
|Détails|L’exécution du workflow conserve un cache des définitions de workflow définies en XOML. SqlTrackingService conserve également un cache qui est indexé par des chaînes. Ces caches sont indexés par les valeurs qui incluent la valeur de hachage de la somme de contrôle. Dans .NET Framework 4.7.2 et versions antérieures, le hachage de somme de contrôle utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS. À partir de la .NET Framework 4,8, l’algorithme utilisé est SHA256. Il ne devrait pas y avoir de problème de compatibilité avec cette modification, car les valeurs sont recalculées chaque fois que l’exécution du workflow et SqlTrackingService démarrent. Toutefois, nous vous proposons des astuces pour permettre aux clients de revenir à l’algorithme de hachage existant, si nécessaire.|
|Suggestion|Si ce changement présente un problème lors de l’exécution de workflows, essayez de définir un commutateur <code>AppContext</code> ou les deux :<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; sur true.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; sur true.</li></ul>En code :<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Ou dans le fichier de configuration (cette opération doit avoir lieu dans le fichier de configuration de l’application qui crée l’objet <xref:System.Workflow.Runtime.WorkflowRuntime>) :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Mineur|
|Version|4.8|
|Tapez|Reciblage|
