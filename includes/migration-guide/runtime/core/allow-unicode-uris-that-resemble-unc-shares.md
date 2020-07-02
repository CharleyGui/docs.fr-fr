---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621063"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="954c3-101">Autoriser les caractères Unicode dans les URI qui ressemblent à des partages UNC</span><span class="sxs-lookup"><span data-stu-id="954c3-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="954c3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="954c3-102">Details</span></span>

<span data-ttu-id="954c3-103">Dans <xref:System.Uri?displayProperty=fullName>, la construction d’un URI de fichier contenant à la fois un nom de partage UNC et des caractères Unicode n’aboutit plus à un URI présentant un état interne non valide.</span><span class="sxs-lookup"><span data-stu-id="954c3-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="954c3-104">Le comportement change uniquement quand toutes les conditions suivantes sont vraies :</span><span class="sxs-lookup"><span data-stu-id="954c3-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="954c3-105">L’URI a le schéma <code>file:</code> et est suivi d’au moins quatre barres obliques.</span><span class="sxs-lookup"><span data-stu-id="954c3-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="954c3-106">Le nom d’hôte commence par un trait de soulignement ou un autre symbole non réservé.</span><span class="sxs-lookup"><span data-stu-id="954c3-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="954c3-107">L’URI contient des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="954c3-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="954c3-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="954c3-108">Suggestion</span></span>

<span data-ttu-id="954c3-109">Les applications qui utilisent des URI contenant systématiquement des caractères Unicode sont susceptibles de suivre ce comportement pour interdire les références à des partages UNC.</span><span class="sxs-lookup"><span data-stu-id="954c3-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="954c3-110">Ces applications doivent utiliser <xref:System.Uri.IsUnc> à la place.</span><span class="sxs-lookup"><span data-stu-id="954c3-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="954c3-111">Nom</span><span class="sxs-lookup"><span data-stu-id="954c3-111">Name</span></span>    | <span data-ttu-id="954c3-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="954c3-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="954c3-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="954c3-113">Scope</span></span>   |<span data-ttu-id="954c3-114">Edge</span><span class="sxs-lookup"><span data-stu-id="954c3-114">Edge</span></span>|
|<span data-ttu-id="954c3-115">Version</span><span class="sxs-lookup"><span data-stu-id="954c3-115">Version</span></span>|<span data-ttu-id="954c3-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="954c3-116">4.7.2</span></span>|
|<span data-ttu-id="954c3-117">Type</span><span class="sxs-lookup"><span data-stu-id="954c3-117">Type</span></span>|<span data-ttu-id="954c3-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="954c3-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="954c3-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="954c3-119">Affected APIs</span></span>

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
