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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="3956b-102">Atténuation : Sérialisation des caractères de contrôle avec le DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="3956b-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="3956b-103">En commençant par .NET Framework 4.7, la façon <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dont les personnages de contrôle sont sérialisés avec le a changé pour se conformer à ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="3956b-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="3956b-104">Impact</span><span class="sxs-lookup"><span data-stu-id="3956b-104">Impact</span></span>

<span data-ttu-id="3956b-105">Dans .NET Framework 4.6.2 et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> les versions antérieures, le n’a pas sérialisé certains personnages de contrôle spéciaux, tels que `\b`, `\f`et `\t`, d’une manière qui était compatible avec les normes ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="3956b-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="3956b-106">Pour les applications qui ciblent les versions de .NET Framework à partir de .NET Framework 4.7, la sérialisation de ces personnages de contrôle est compatible avec ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="3956b-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="3956b-107">Les API suivantes sont concernées :</span><span class="sxs-lookup"><span data-stu-id="3956b-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="3956b-108">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="3956b-108">Mitigation</span></span>

<span data-ttu-id="3956b-109">Pour les applications qui ciblent les versions de .NET Framework à partir de .NET Framework 4.7, ce comportement est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="3956b-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="3956b-110">Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="3956b-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="3956b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3956b-111">See also</span></span>

- [<span data-ttu-id="3956b-112">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="3956b-112">Application compatibility</span></span>](application-compatibility.md)
