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
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="778a5-102">Atténuation : sérialisation des caractères de contrôle avec DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="778a5-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="778a5-103">À compter de .NET Framework 4,7, la façon dont les caractères de contrôle sont sérialisés avec le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a changé pour être conforme à ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="778a5-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="778a5-104">Impact</span><span class="sxs-lookup"><span data-stu-id="778a5-104">Impact</span></span>

<span data-ttu-id="778a5-105">Dans .NET Framework 4.6.2 et les versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> n’a pas sérialisé certains caractères de contrôle spéciaux, tels que `\b`, `\f`et `\t`, d’une manière compatible avec les normes ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="778a5-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="778a5-106">Pour les applications qui ciblent des versions de .NET Framework à partir de .NET Framework 4,7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="778a5-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="778a5-107">Les API suivantes sont concernées :</span><span class="sxs-lookup"><span data-stu-id="778a5-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="778a5-108">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="778a5-108">Mitigation</span></span>

<span data-ttu-id="778a5-109">Pour les applications qui ciblent des versions de .NET Framework à partir de .NET Framework 4,7, ce comportement est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="778a5-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="778a5-110">Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="778a5-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="778a5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="778a5-111">See also</span></span>

- [<span data-ttu-id="778a5-112">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="778a5-112">Application compatibility</span></span>](application-compatibility.md)
