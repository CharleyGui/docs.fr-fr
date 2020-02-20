---
ms.openlocfilehash: 2c532bf3778b940f68db859420dd12826e9da388
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466051"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>La sérialisation des caractères de contrôle avec DataContractJsonSerializer est désormais compatible avec ECMAScript V6 et V8

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6.2 et les versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> n’a pas sérialisé certains caractères de contrôle spéciaux, tels que \b, \f et \t, d’une manière compatible avec les normes ECMAScript V6 et V8. À compter de .NET Framework 4,7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.|
|Suggestion|Pour les applications qui ciblent .NET. Framework 4.7, cette fonctionnalité est activée par défaut. Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config ou au fichier web.config :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4,7|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|
