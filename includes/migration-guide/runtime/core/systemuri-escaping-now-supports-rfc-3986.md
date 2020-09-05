---
ms.openlocfilehash: e7001fcfdf88fd9e710fbb702f2ed39d63b1e080
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497703"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a><span data-ttu-id="10a2f-101">L’échappement de System.Uri prend maintenant en charge la norme RFC 3986</span><span class="sxs-lookup"><span data-stu-id="10a2f-101">System.Uri escaping now supports RFC 3986</span></span>

#### <a name="details"></a><span data-ttu-id="10a2f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="10a2f-102">Details</span></span>

<span data-ttu-id="10a2f-103">L’échappement d’URI a été modifié dans NET Framework 4.5 de manière à prendre en charge la norme [RFC 3986](https://tools.ietf.org/html/rfc3986).</span><span class="sxs-lookup"><span data-stu-id="10a2f-103">URI escaping has changed in .NET Framework 4.5 to support [RFC 3986](https://tools.ietf.org/html/rfc3986).</span></span> <span data-ttu-id="10a2f-104">Ces modifications sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="10a2f-104">Specific changes include:</span></span><ul><li><span data-ttu-id="10a2f-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> représente une séquence d'échappement pour les caractères réservés basés sur la norme RFC 3986.</span><span class="sxs-lookup"><span data-stu-id="10a2f-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> escapes reserved characters based on RFC 3986.</span></span></li><li><span data-ttu-id="10a2f-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> ne représente pas une séquence d'échappement pour les caractères réservés.</span><span class="sxs-lookup"><span data-stu-id="10a2f-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> does not escape reserved characters.</span></span></li><li><span data-ttu-id="10a2f-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> ne lève pas d'exception s'il rencontre une séquence d'échappement non valide.</span><span class="sxs-lookup"><span data-stu-id="10a2f-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> does not throw an exception if it encounters an invalid escape sequence.</span></span></li><li><span data-ttu-id="10a2f-108">Les caractères d'échappement non réservés sont sans séquence d'échappement.</span><span class="sxs-lookup"><span data-stu-id="10a2f-108">Unreserved escaped characters are un-escaped.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="10a2f-109">Suggestion</span><span class="sxs-lookup"><span data-stu-id="10a2f-109">Suggestion</span></span>

<ul><li><span data-ttu-id="10a2f-110">Mettez à jour les applications pour qu’elles ne comptent pas sur <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> pour lever une exception en cas de séquence d’échappement non valide.</span><span class="sxs-lookup"><span data-stu-id="10a2f-110">Update applications to not rely on <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> to throw in the case of an invalid escape sequence.</span></span> <span data-ttu-id="10a2f-111">Ces séquences sont à présent directement détectées.</span><span class="sxs-lookup"><span data-stu-id="10a2f-111">Such sequences must be detected directly now.</span></span></li><li><span data-ttu-id="10a2f-112">Il est également possible que les URI avec et sans séquence d’échappement, ainsi que les chaînes de données, varient entre les versions 4.0 et 4.5 du .NET Framework. De plus, ils ne doivent pas être comparés directement entre différentes versions de .NET.</span><span class="sxs-lookup"><span data-stu-id="10a2f-112">Similarly, expect that Escaped and Unescaped URI and Data strings may vary from .NET Framework 4.0 and .NET Framework 4.5 and should not be compared across .NET versions directly.</span></span> <span data-ttu-id="10a2f-113">Ils doivent être analysés et normalisés dans une seule version du .NET avant de faire l’objet d’une comparaison.</span><span class="sxs-lookup"><span data-stu-id="10a2f-113">Instead, they should be parsed and normalized in a single .NET version before any comparisons are made.</span></span></li></ul>

| <span data-ttu-id="10a2f-114">Name</span><span class="sxs-lookup"><span data-stu-id="10a2f-114">Name</span></span>    | <span data-ttu-id="10a2f-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="10a2f-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="10a2f-116">Étendue</span><span class="sxs-lookup"><span data-stu-id="10a2f-116">Scope</span></span>   |<span data-ttu-id="10a2f-117">Secondaire</span><span class="sxs-lookup"><span data-stu-id="10a2f-117">Minor</span></span>|
|<span data-ttu-id="10a2f-118">Version</span><span class="sxs-lookup"><span data-stu-id="10a2f-118">Version</span></span>|<span data-ttu-id="10a2f-119">4,5</span><span class="sxs-lookup"><span data-stu-id="10a2f-119">4.5</span></span>|
|<span data-ttu-id="10a2f-120">Type</span><span class="sxs-lookup"><span data-stu-id="10a2f-120">Type</span></span>|<span data-ttu-id="10a2f-121">Runtime</span><span class="sxs-lookup"><span data-stu-id="10a2f-121">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="10a2f-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="10a2f-122">Affected APIs</span></span>

- <xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.EscapeDataString(System.String)`
- `M:System.Uri.EscapeUriString(System.String)`
- `M:System.Uri.UnescapeDataString(System.String)`

-->
