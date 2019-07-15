---
ms.openlocfilehash: 2f5511b7694f91893b731805119b85d1a5669a33
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859114"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>La sérialisation des caractères de contrôle avec DataContractJsonSerializer est maintenant compatible avec ECMAScript V6 et V8

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6.2 et antérieur, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> ne sérialisait pas certains caractères de contrôle spéciaux, comme \b, \f et \t, d’une manière compatible avec les normes ECMAScript V6 et V8. À compter de .NET Framework 4.7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.|
|Suggestion|Pour les applications qui ciblent .NET. Framework 4.7, cette fonctionnalité est activée par défaut. Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config ou au fichier web.config :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Portée|Microsoft Edge|
|Version|4.7|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

