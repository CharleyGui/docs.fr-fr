---
title: Sérialisation de caractères de contrôle avec DataContractJsonSerializer
description: En savoir plus sur la façon dont la sérialisation des caractères de contrôle a changé pour être conforme à ECMAScript V6 et V8 dans .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475383"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="81342-103">Atténuation : sérialisation des caractères de contrôle avec DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="81342-103">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="81342-104">À compter de .NET Framework 4,7, la façon dont les caractères de contrôle sont sérialisés avec <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a changé pour être conforme à ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="81342-104">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="81342-105">Impact</span><span class="sxs-lookup"><span data-stu-id="81342-105">Impact</span></span>

<span data-ttu-id="81342-106">Dans .NET Framework 4.6.2 et les versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> n’a pas sérialisé certains caractères de contrôle spéciaux, tels que `\b` , `\f` et `\t` , d’une manière compatible avec les normes ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="81342-106">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="81342-107">Pour les applications qui ciblent des versions de .NET Framework à partir de .NET Framework 4,7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="81342-107">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="81342-108">Les API suivantes sont concernées :</span><span class="sxs-lookup"><span data-stu-id="81342-108">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="81342-109">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="81342-109">Mitigation</span></span>

<span data-ttu-id="81342-110">Pour les applications qui ciblent des versions de .NET Framework à partir de .NET Framework 4,7, ce comportement est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="81342-110">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="81342-111">Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="81342-111">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="81342-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81342-112">See also</span></span>

- [<span data-ttu-id="81342-113">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="81342-113">Application compatibility</span></span>](application-compatibility.md)
