---
title: Sérialisation des personnages de contrôle avec DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181210"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Atténuation : Sérialisation des caractères de contrôle avec le DataContractJsonSerializer

En commençant par .NET Framework 4.7, la façon <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dont les personnages de contrôle sont sérialisés avec le a changé pour se conformer à ECMAScript V6 et V8.

## <a name="impact"></a>Impact

Dans .NET Framework 4.6.2 et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> les versions antérieures, le n’a pas sérialisé certains personnages de contrôle spéciaux, tels que `\b`, `\f`et `\t`, d’une manière qui était compatible avec les normes ECMAScript V6 et V8.

Pour les applications qui ciblent les versions de .NET Framework à partir de .NET Framework 4.7, la sérialisation de ces personnages de contrôle est compatible avec ECMAScript V6 et V8. Les API suivantes sont concernées :

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Limitation des risques

Pour les applications qui ciblent les versions de .NET Framework à partir de .NET Framework 4.7, ce comportement est activé par défaut.

Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
