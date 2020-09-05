---
ms.openlocfilehash: 6f22d6211ec9238fd1c7786643ca95db02bfca64
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497487"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="f0cf4-101">Les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur</span><span class="sxs-lookup"><span data-stu-id="f0cf4-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="f0cf4-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f0cf4-102">Details</span></span>

<span data-ttu-id="f0cf4-103">À compter de .NET Framework 4.5, les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur (objet <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="f0cf4-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="f0cf4-104">La tentative de sérialisation d'un catalogue MEF lève une exception.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f0cf4-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f0cf4-105">Suggestion</span></span>

<span data-ttu-id="f0cf4-106">Ne peut plus utiliser un catalogue MEF pour créer un sérialiseur</span><span class="sxs-lookup"><span data-stu-id="f0cf4-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="f0cf4-107">Name</span><span class="sxs-lookup"><span data-stu-id="f0cf4-107">Name</span></span>    | <span data-ttu-id="f0cf4-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="f0cf4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0cf4-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="f0cf4-109">Scope</span></span>   |<span data-ttu-id="f0cf4-110">Majeure</span><span class="sxs-lookup"><span data-stu-id="f0cf4-110">Major</span></span>|
|<span data-ttu-id="f0cf4-111">Version</span><span class="sxs-lookup"><span data-stu-id="f0cf4-111">Version</span></span>|<span data-ttu-id="f0cf4-112">4,5</span><span class="sxs-lookup"><span data-stu-id="f0cf4-112">4.5</span></span>|
|<span data-ttu-id="f0cf4-113">Type</span><span class="sxs-lookup"><span data-stu-id="f0cf4-113">Type</span></span>|<span data-ttu-id="f0cf4-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="f0cf4-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f0cf4-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="f0cf4-115">Affected APIs</span></span>

<span data-ttu-id="f0cf4-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
