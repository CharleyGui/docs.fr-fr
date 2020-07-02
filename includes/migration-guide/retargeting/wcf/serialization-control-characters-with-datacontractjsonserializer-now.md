---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614530"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a><span data-ttu-id="db881-101">La sérialisation des caractères de contrôle avec DataContractJsonSerializer est désormais compatible avec ECMAScript V6 et V8</span><span class="sxs-lookup"><span data-stu-id="db881-101">Serialization of control characters with DataContractJsonSerializer is now compatible with ECMAScript V6 and V8</span></span>

#### <a name="details"></a><span data-ttu-id="db881-102">Détails</span><span class="sxs-lookup"><span data-stu-id="db881-102">Details</span></span>

<span data-ttu-id="db881-103">Dans .NET Framework 4.6.2 et les versions antérieures, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> n’a pas sérialisé certains caractères de contrôle spéciaux, tels que \b, \f et \t, d’une manière compatible avec les normes ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="db881-103">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> did not serialize some special control characters, such as \b, \f, and \t, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span> <span data-ttu-id="db881-104">À compter de .NET Framework 4,7, la sérialisation de ces caractères de contrôle est compatible avec ECMAScript V6 et V8.</span><span class="sxs-lookup"><span data-stu-id="db881-104">Starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="db881-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="db881-105">Suggestion</span></span>

<span data-ttu-id="db881-106">Pour les applications qui ciblent .NET. Framework 4.7, cette fonctionnalité est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="db881-106">For apps that target the .NET Framework 4.7, this feature is enabled by default.</span></span> <span data-ttu-id="db881-107">Si ce comportement n’est pas souhaitable, vous pouvez désactiver cette fonctionnalité en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou au fichier web.config :</span><span class="sxs-lookup"><span data-stu-id="db881-107">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| <span data-ttu-id="db881-108">Nom</span><span class="sxs-lookup"><span data-stu-id="db881-108">Name</span></span>    | <span data-ttu-id="db881-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="db881-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="db881-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="db881-110">Scope</span></span>   | <span data-ttu-id="db881-111">Edge</span><span class="sxs-lookup"><span data-stu-id="db881-111">Edge</span></span>        |
| <span data-ttu-id="db881-112">Version</span><span class="sxs-lookup"><span data-stu-id="db881-112">Version</span></span> | <span data-ttu-id="db881-113">4,7</span><span class="sxs-lookup"><span data-stu-id="db881-113">4.7</span></span>         |
| <span data-ttu-id="db881-114">Type</span><span class="sxs-lookup"><span data-stu-id="db881-114">Type</span></span>    | <span data-ttu-id="db881-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="db881-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="db881-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="db881-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
