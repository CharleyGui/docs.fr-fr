---
title: 'Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: 5f8218d0f369f25b1add501fdc975d6dccfe90fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126149"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="5c21d-102">Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="5c21d-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="5c21d-103">À compter du .NET Framework 4.7, la manière dont les caractères de contrôle sont sérialisés avec le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a changé pour être conforme à ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="5c21d-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="5c21d-104">Impact</span><span class="sxs-lookup"><span data-stu-id="5c21d-104">Impact</span></span>

<span data-ttu-id="5c21d-105">Dans le .NET Framework 4.6.2 et versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne sérialise pas certains caractères de contrôle spéciaux, comme `\b`, `\f` et `\t`, d’une manière compatible avec les normes ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="5c21d-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="5c21d-106">Pour les applications qui ciblent des versions de .NET Framework ultérieures à 4.7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="5c21d-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="5c21d-107">Les API suivantes sont concernées :</span><span class="sxs-lookup"><span data-stu-id="5c21d-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="5c21d-108">Atténuation</span><span class="sxs-lookup"><span data-stu-id="5c21d-108">Mitigation</span></span>

<span data-ttu-id="5c21d-109">Pour les applications qui ciblent des versions de .NET Framework ultérieures à la 4.7, ce comportement est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="5c21d-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="5c21d-110">Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="5c21d-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="5c21d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c21d-111">See also</span></span>

- [<span data-ttu-id="5c21d-112">Reciblage des modifications dans le .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="5c21d-112">Retargeting Changes in the .NET Framework 4.7</span></span>](retargeting-changes-in-the-net-framework-4-7.md)
