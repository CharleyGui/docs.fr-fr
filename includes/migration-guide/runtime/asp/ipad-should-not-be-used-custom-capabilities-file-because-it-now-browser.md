---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619943"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="101ab-101">IPad ne doit pas servir dans le fichier de fonctionnalités personnalisé, car il est désormais une fonctionnalité du navigateur</span><span class="sxs-lookup"><span data-stu-id="101ab-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

#### <a name="details"></a><span data-ttu-id="101ab-102">Détails</span><span class="sxs-lookup"><span data-stu-id="101ab-102">Details</span></span>

<span data-ttu-id="101ab-103">À compter de .NET Framework 4.5, iPad étant un identificateur dans le fichier de fonctionnalités du navigateur ASP.NET par défaut, il ne doit pas être utilisé dans un fichier de fonctionnalités personnalisé</span><span class="sxs-lookup"><span data-stu-id="101ab-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>

#### <a name="suggestion"></a><span data-ttu-id="101ab-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="101ab-104">Suggestion</span></span>

<span data-ttu-id="101ab-105">Si des fonctionnalités spécifiques à l’iPad sont requises, il est nécessaire de modifier le comportement de l’iPad en définissant des fonctionnalités sur la passerelle prédéfinie refID &quot;IPad&quot; et non en générant un ID &quot;IPad&quot; par mise en correspondance de l’agent utilisateur.</span><span class="sxs-lookup"><span data-stu-id="101ab-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>

| <span data-ttu-id="101ab-106">Nom</span><span class="sxs-lookup"><span data-stu-id="101ab-106">Name</span></span>    | <span data-ttu-id="101ab-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="101ab-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="101ab-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="101ab-108">Scope</span></span>   |<span data-ttu-id="101ab-109">Edge</span><span class="sxs-lookup"><span data-stu-id="101ab-109">Edge</span></span>|
|<span data-ttu-id="101ab-110">Version</span><span class="sxs-lookup"><span data-stu-id="101ab-110">Version</span></span>|<span data-ttu-id="101ab-111">4,5</span><span class="sxs-lookup"><span data-stu-id="101ab-111">4.5</span></span>|
|<span data-ttu-id="101ab-112">Type</span><span class="sxs-lookup"><span data-stu-id="101ab-112">Type</span></span>|<span data-ttu-id="101ab-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="101ab-113">Runtime</span></span>|
