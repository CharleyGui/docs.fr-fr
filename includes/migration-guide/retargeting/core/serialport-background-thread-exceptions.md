---
ms.openlocfilehash: 81b104d8e5a9ccc8e790c3b16e4837cfa0c0def5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859025"
---
### <a name="serialport-background-thread-exceptions"></a>Exceptions de thread d’arrière-plan SerialPort

|   |   |
|---|---|
|Détails|Les threads d’arrière-plan créés avec des flux <xref:System.IO.Ports.SerialPort> ne terminent plus le processus quand des exceptions de système d’exploitation sont levées. <br/>Dans les applications qui ciblent .NET Framework 4.7 et les versions antérieures, un processus est terminé quand une exception de système d’exploitation est levée sur un thread d’arrière-plan créé avec un flux <xref:System.IO.Ports.SerialPort>. <br/>Dans les applications qui ciblent .NET Framework 4.7.1 ou une version ultérieure, les threads d’arrière-plan attendent la fin des événements de système d’exploitation liés au port série actif et peuvent planter dans certains cas, comme la suppression soudaine du port série.|
|Suggestion|Pour les applications qui ciblent .NET Framework 4.7.1, vous pouvez refuser la gestion des exceptions en ajoutant le code suivant à la section <code>&lt;runtime&gt;</code> de votre fichier <code>app.config</code> :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pour les applications qui ciblent des versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.7.1 ou une version ultérieure, vous pouvez accepter la prise en charge de la gestion des exceptions en ajoutant le code suivant à la section <code>&lt;runtime&gt;</code> de votre fichier <code>app.config</code> :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.7.1|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|
