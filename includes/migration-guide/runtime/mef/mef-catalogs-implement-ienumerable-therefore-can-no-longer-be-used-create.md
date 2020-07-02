---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620034"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="3f24e-101">Les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur</span><span class="sxs-lookup"><span data-stu-id="3f24e-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="3f24e-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3f24e-102">Details</span></span>

<span data-ttu-id="3f24e-103">À compter de .NET Framework 4.5, les catalogues MEF implémentent IEnumerable et ne peuvent donc plus être utilisés pour créer un sérialiseur (objet <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="3f24e-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="3f24e-104">La tentative de sérialisation d'un catalogue MEF lève une exception.</span><span class="sxs-lookup"><span data-stu-id="3f24e-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3f24e-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3f24e-105">Suggestion</span></span>

<span data-ttu-id="3f24e-106">Ne peut plus utiliser un catalogue MEF pour créer un sérialiseur</span><span class="sxs-lookup"><span data-stu-id="3f24e-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="3f24e-107">Nom</span><span class="sxs-lookup"><span data-stu-id="3f24e-107">Name</span></span>    | <span data-ttu-id="3f24e-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="3f24e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3f24e-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="3f24e-109">Scope</span></span>   |<span data-ttu-id="3f24e-110">Majeure</span><span class="sxs-lookup"><span data-stu-id="3f24e-110">Major</span></span>|
|<span data-ttu-id="3f24e-111">Version</span><span class="sxs-lookup"><span data-stu-id="3f24e-111">Version</span></span>|<span data-ttu-id="3f24e-112">4,5</span><span class="sxs-lookup"><span data-stu-id="3f24e-112">4.5</span></span>|
|<span data-ttu-id="3f24e-113">Type</span><span class="sxs-lookup"><span data-stu-id="3f24e-113">Type</span></span>|<span data-ttu-id="3f24e-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="3f24e-114">Runtime</span></span>|
