---
ms.openlocfilehash: 3506653bfc749ae3d8002715ca72ca89de7a681b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91024847"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="4e7e9-101">AddressHeaderCollection dans WCF lève maintenant une exception ArgumentException si un élément addressHeader a la valeur Null</span><span class="sxs-lookup"><span data-stu-id="4e7e9-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="4e7e9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4e7e9-102">Details</span></span>

<span data-ttu-id="4e7e9-103">À compter de .NET Framework 4.7.1, le constructeur <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> lève une <xref:System.ArgumentException> si l’un des éléments a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="4e7e9-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="4e7e9-104">Dans .NET Framework 4.7 et versions antérieures, aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="4e7e9-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4e7e9-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4e7e9-105">Suggestion</span></span>

<span data-ttu-id="4e7e9-106">Si vous rencontrez des problèmes de compatibilité avec cette modification sur le .NET Framework 4.7.1 ou une version ultérieure, vous pouvez choisir de l’annuler en ajoutant la ligne suivante à la `<runtime>` section du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="4e7e9-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="4e7e9-107">Nom</span><span class="sxs-lookup"><span data-stu-id="4e7e9-107">Name</span></span>    | <span data-ttu-id="4e7e9-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="4e7e9-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="4e7e9-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="4e7e9-109">Scope</span></span>   | <span data-ttu-id="4e7e9-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="4e7e9-110">Minor</span></span>   |
| <span data-ttu-id="4e7e9-111">Version</span><span class="sxs-lookup"><span data-stu-id="4e7e9-111">Version</span></span> | <span data-ttu-id="4e7e9-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="4e7e9-112">4.7.1</span></span>   |
| <span data-ttu-id="4e7e9-113">Type</span><span class="sxs-lookup"><span data-stu-id="4e7e9-113">Type</span></span>    | <span data-ttu-id="4e7e9-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="4e7e9-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4e7e9-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="4e7e9-115">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
