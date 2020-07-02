---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616247"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>La définition XOML du workflow et les clés de cache SqlTrackingService sont passées de MD5 à SHA256

#### <a name="details"></a>Détails

L’exécution du workflow conserve un cache des définitions de workflow définies en XOML. SqlTrackingService conserve également un cache qui est indexé par des chaînes. Ces caches sont indexés par les valeurs qui incluent la valeur de hachage de la somme de contrôle. Dans .NET Framework 4.7.2 et versions antérieures, le hachage de somme de contrôle utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS. À partir de la .NET Framework 4,8, l’algorithme utilisé est SHA256. Il ne devrait pas y avoir de problème de compatibilité avec cette modification, car les valeurs sont recalculées chaque fois que l’exécution du workflow et SqlTrackingService démarrent. Toutefois, nous vous proposons des astuces pour permettre aux clients de revenir à l’algorithme de hachage existant, si nécessaire.

#### <a name="suggestion"></a>Suggestion

Si ce changement présente un problème lors de l’exécution de workflows, essayez de définir un commutateur `AppContext` ou les deux :

- &quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; sur true.
- &quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; sur true.
Dans le code :

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

Ou dans le fichier de configuration (cette opération doit avoir lieu dans le fichier de configuration de l’application qui crée l’objet <xref:System.Workflow.Runtime.WorkflowRuntime>) :

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.8         |
| Type    | Reciblage |
