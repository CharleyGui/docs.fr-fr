---
title: Sérialisation de caractères de contrôle avec DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 209f7827e61ef72de1d64fad46dc9f241fa6edef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346570"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="07e39-102">Atténuation : sérialisation des caractères de contrôle avec DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="07e39-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="07e39-103">À compter du .NET Framework 4.7, la manière dont les caractères de contrôle sont sérialisés avec le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a changé pour être conforme à ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="07e39-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="07e39-104">Impact</span><span class="sxs-lookup"><span data-stu-id="07e39-104">Impact</span></span>

<span data-ttu-id="07e39-105">Dans le .NET Framework 4.6.2 et versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne sérialise pas certains caractères de contrôle spéciaux, comme `\b`, `\f` et `\t`, d’une manière compatible avec les normes ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="07e39-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="07e39-106">Pour les applications qui ciblent des versions de .NET Framework ultérieures à 4.7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="07e39-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="07e39-107">Les API suivantes sont concernées :</span><span class="sxs-lookup"><span data-stu-id="07e39-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="07e39-108">Atténuation</span><span class="sxs-lookup"><span data-stu-id="07e39-108">Mitigation</span></span>

<span data-ttu-id="07e39-109">Pour les applications qui ciblent des versions de .NET Framework ultérieures à la 4.7, ce comportement est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="07e39-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="07e39-110">Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="07e39-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="07e39-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07e39-111">See also</span></span>

- [<span data-ttu-id="07e39-112">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="07e39-112">Application compatibility</span></span>](application-compatibility.md)
