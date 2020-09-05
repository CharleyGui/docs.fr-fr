---
ms.openlocfilehash: 1047f4028697a73741470d1aac8b3aeed37be217
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496833"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="9e1d7-101">Autoriser les caractères Unicode dans les URI qui ressemblent à des partages UNC</span><span class="sxs-lookup"><span data-stu-id="9e1d7-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="9e1d7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="9e1d7-102">Details</span></span>

<span data-ttu-id="9e1d7-103">Dans <xref:System.Uri?displayProperty=fullName>, la construction d’un URI de fichier contenant à la fois un nom de partage UNC et des caractères Unicode n’aboutit plus à un URI présentant un état interne non valide.</span><span class="sxs-lookup"><span data-stu-id="9e1d7-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="9e1d7-104">Le comportement change uniquement quand toutes les conditions suivantes sont vraies :</span><span class="sxs-lookup"><span data-stu-id="9e1d7-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="9e1d7-105">L’URI a le schéma <code>file:</code> et est suivi d’au moins quatre barres obliques.</span><span class="sxs-lookup"><span data-stu-id="9e1d7-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="9e1d7-106">Le nom d’hôte commence par un trait de soulignement ou un autre symbole non réservé.</span><span class="sxs-lookup"><span data-stu-id="9e1d7-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="9e1d7-107">L’URI contient des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="9e1d7-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="9e1d7-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="9e1d7-108">Suggestion</span></span>

<span data-ttu-id="9e1d7-109">Les applications qui utilisent des URI contenant systématiquement des caractères Unicode sont susceptibles de suivre ce comportement pour interdire les références à des partages UNC.</span><span class="sxs-lookup"><span data-stu-id="9e1d7-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="9e1d7-110">Ces applications doivent utiliser <xref:System.Uri.IsUnc> à la place.</span><span class="sxs-lookup"><span data-stu-id="9e1d7-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="9e1d7-111">Name</span><span class="sxs-lookup"><span data-stu-id="9e1d7-111">Name</span></span>    | <span data-ttu-id="9e1d7-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="9e1d7-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9e1d7-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="9e1d7-113">Scope</span></span>   |<span data-ttu-id="9e1d7-114">Edge</span><span class="sxs-lookup"><span data-stu-id="9e1d7-114">Edge</span></span>|
|<span data-ttu-id="9e1d7-115">Version</span><span class="sxs-lookup"><span data-stu-id="9e1d7-115">Version</span></span>|<span data-ttu-id="9e1d7-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="9e1d7-116">4.7.2</span></span>|
|<span data-ttu-id="9e1d7-117">Type</span><span class="sxs-lookup"><span data-stu-id="9e1d7-117">Type</span></span>|<span data-ttu-id="9e1d7-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="9e1d7-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="9e1d7-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="9e1d7-119">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Uri`

-->
