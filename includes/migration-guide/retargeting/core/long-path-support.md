---
ms.openlocfilehash: 506218195417548880a9d8d10508a570a7769682
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859353"
---
### <a name="long-path-support"></a>Prise en charge des chemins d’accès longs

|   |   |
|---|---|
|Détails|À partir des applications qui ciblent .NET Framework 4.6.2, les chemins longs (comprenant jusqu’à 32 000 caractères) sont pris en charge et la limite de 260 caractères (ou <code>MAX_PATH</code>) sur la longueur du chemin est supprimée. Pour les applications qui sont recompilées pour cibler .NET Framework 4.6.2, les chemins de code qui levaient précédemment un <xref:System.IO.PathTooLongException?displayProperty=name> car un chemin dépassait 260 caractères lèvent désormais un <xref:System.IO.PathTooLongException?displayProperty=name> uniquement quand les conditions suivantes sont remplies :<ul><li>La longueur du chemin est supérieure à <xref:System.Int16.MaxValue> (32 767) caractères.</li><li>Le système d’exploitation renvoie <code>COR_E_PATHTOOLONG</code> ou son équivalent.</li></ul>Pour les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, le runtime levait automatiquement un <xref:System.IO.PathTooLongException?displayProperty=name> chaque fois qu’un chemin comportait plus de 260 caractères.|
|Suggestion|Pour les applications qui ciblent .NET Framework 4.6.2, vous pouvez refuser la prise en charge des chemins longs en ajoutant le code suivant à la section <code>&lt;runtime&gt;</code> de votre fichier <code>app.config</code> :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pour les applications qui ciblent des versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure, vous pouvez accepter la prise en charge des chemins longs en ajoutant le code suivant à la section <code>&lt;runtime&gt;</code> de votre fichier <code>app.config</code> :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.6.2|
|Type|Reciblage|
