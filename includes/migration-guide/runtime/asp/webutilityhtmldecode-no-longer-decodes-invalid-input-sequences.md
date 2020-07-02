---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619932"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="4dab8-101">WebUtility.HtmlDecode ne décode plus les séquences d’entrée non valides</span><span class="sxs-lookup"><span data-stu-id="4dab8-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="4dab8-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4dab8-102">Details</span></span>

<span data-ttu-id="4dab8-103">Par défaut, les méthodes de décodage ne décodent plus une séquence d'entrée non valide en une chaîne UTF-16 non valide.</span><span class="sxs-lookup"><span data-stu-id="4dab8-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="4dab8-104">Au lieu de cela, elles retournent l'entrée d'origine.</span><span class="sxs-lookup"><span data-stu-id="4dab8-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4dab8-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4dab8-105">Suggestion</span></span>

<span data-ttu-id="4dab8-106">Le changement lié à la sortie du décodeur doit importer uniquement si vous stockez des données binaires à la place de données UTF-16 dans les chaînes.</span><span class="sxs-lookup"><span data-stu-id="4dab8-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="4dab8-107">Pour contrôler explicitement ce comportement, affectez à l’attribut <code>aspnet:AllowRelaxedUnicodeDecoding</code> de l’élément [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) la valeur <code>true</code> pour activer le comportement hérité ou la valeur <code>false</code> pour activer le comportement actuel.</span><span class="sxs-lookup"><span data-stu-id="4dab8-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="4dab8-108">Nom</span><span class="sxs-lookup"><span data-stu-id="4dab8-108">Name</span></span>    | <span data-ttu-id="4dab8-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="4dab8-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4dab8-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="4dab8-110">Scope</span></span>   |<span data-ttu-id="4dab8-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="4dab8-111">Minor</span></span>|
|<span data-ttu-id="4dab8-112">Version</span><span class="sxs-lookup"><span data-stu-id="4dab8-112">Version</span></span>|<span data-ttu-id="4dab8-113">4,5</span><span class="sxs-lookup"><span data-stu-id="4dab8-113">4.5</span></span>|
|<span data-ttu-id="4dab8-114">Type</span><span class="sxs-lookup"><span data-stu-id="4dab8-114">Type</span></span>|<span data-ttu-id="4dab8-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="4dab8-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4dab8-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="4dab8-116">Affected APIs</span></span>

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
