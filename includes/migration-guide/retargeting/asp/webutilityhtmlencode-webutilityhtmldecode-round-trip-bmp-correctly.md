---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617163"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="a1fb7-101">WebUtility.HtmlEncode et WebUtility.HtmlDecode font un aller-retour correct au plan BMP</span><span class="sxs-lookup"><span data-stu-id="a1fb7-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

#### <a name="details"></a><span data-ttu-id="a1fb7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a1fb7-102">Details</span></span>

<span data-ttu-id="a1fb7-103">Pour les applications qui ciblent .NET Framework 4.5, les caractères extérieurs au plan BMP (Basic Multilingual Plane) font un aller-retour correct quand ils sont passés à la méthode <xref:System.Net.WebUtility.HtmlDecode(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="a1fb7-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a1fb7-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a1fb7-104">Suggestion</span></span>

<span data-ttu-id="a1fb7-105">Cette modification ne doit avoir aucun effet sur les applications actuelles, mais pour restaurer le comportement d’origine, affectez `targetFramework` à l’attribut de l' `<httpRuntime>` élément une chaîne autre que « 4,5 ».</span><span class="sxs-lookup"><span data-stu-id="a1fb7-105">This change should have no effect on current applications, but to restore the original behavior, set the `targetFramework` attribute of the `<httpRuntime>` element to a string other than "4.5".</span></span> <span data-ttu-id="a1fb7-106">Vous pouvez également définir les attributs `unicodeEncodingConformance` et `unicodeDecodingConformance` de l'élément de configuration `<webUtility>` pour contrôler ce comportement indépendamment de la version ciblée du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1fb7-106">You can also set the `unicodeEncodingConformance` and `unicodeDecodingConformance` attributes of the `<webUtility>` configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>

| <span data-ttu-id="a1fb7-107">Nom</span><span class="sxs-lookup"><span data-stu-id="a1fb7-107">Name</span></span>    | <span data-ttu-id="a1fb7-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="a1fb7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a1fb7-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="a1fb7-109">Scope</span></span>   | <span data-ttu-id="a1fb7-110">Edge</span><span class="sxs-lookup"><span data-stu-id="a1fb7-110">Edge</span></span>        |
| <span data-ttu-id="a1fb7-111">Version</span><span class="sxs-lookup"><span data-stu-id="a1fb7-111">Version</span></span> | <span data-ttu-id="a1fb7-112">4,5</span><span class="sxs-lookup"><span data-stu-id="a1fb7-112">4.5</span></span>         |
| <span data-ttu-id="a1fb7-113">Type</span><span class="sxs-lookup"><span data-stu-id="a1fb7-113">Type</span></span>    | <span data-ttu-id="a1fb7-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="a1fb7-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a1fb7-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="a1fb7-115">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
