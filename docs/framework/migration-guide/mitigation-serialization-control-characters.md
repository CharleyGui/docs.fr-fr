---
title: Sérialisation de caractères de contrôle avec DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b6468bc4ae37765d969a1f92b16967cc656ab7ff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452628"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Atténuation : sérialisation des caractères de contrôle avec DataContractJsonSerializer

À compter de .NET Framework 4,7, la façon dont les caractères de contrôle sont sérialisés avec le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a changé pour être conforme à ECMAScript V6 et V8. 
 
## <a name="impact"></a>Impact

Dans .NET Framework 4.6.2 et les versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> n’a pas sérialisé certains caractères de contrôle spéciaux, tels que `\b`, `\f`et `\t`, d’une manière compatible avec les normes ECMAScript V6 et V8.

Pour les applications qui ciblent des versions de .NET Framework à partir de .NET Framework 4,7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8. Les API suivantes sont concernées :

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Limitation des risques

Pour les applications qui ciblent des versions de .NET Framework à partir de .NET Framework 4,7, ce comportement est activé par défaut.

Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
