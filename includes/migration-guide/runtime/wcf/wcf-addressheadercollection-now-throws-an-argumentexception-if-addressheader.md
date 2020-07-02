---
ms.openlocfilehash: d29be721b50d1c93723b325774a06e86f77dbebf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621092"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="6c978-101">AddressHeaderCollection dans WCF lève maintenant une exception ArgumentException si un élément addressHeader a la valeur Null</span><span class="sxs-lookup"><span data-stu-id="6c978-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="6c978-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6c978-102">Details</span></span>

<span data-ttu-id="6c978-103">À compter de .NET Framework 4.7.1, le constructeur <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> lève une <xref:System.ArgumentException> si l’un des éléments a la valeur <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="6c978-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="6c978-104">Dans .NET Framework 4.7 et versions antérieures, aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="6c978-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6c978-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6c978-105">Suggestion</span></span>

<span data-ttu-id="6c978-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas y adhérer en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="6c978-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="6c978-107">Nom</span><span class="sxs-lookup"><span data-stu-id="6c978-107">Name</span></span>    | <span data-ttu-id="6c978-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="6c978-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6c978-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="6c978-109">Scope</span></span>   |<span data-ttu-id="6c978-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="6c978-110">Minor</span></span>|
|<span data-ttu-id="6c978-111">Version</span><span class="sxs-lookup"><span data-stu-id="6c978-111">Version</span></span>|<span data-ttu-id="6c978-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="6c978-112">4.7.1</span></span>|
|<span data-ttu-id="6c978-113">Type</span><span class="sxs-lookup"><span data-stu-id="6c978-113">Type</span></span>|<span data-ttu-id="6c978-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="6c978-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6c978-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="6c978-115">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
