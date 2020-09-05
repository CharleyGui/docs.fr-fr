---
ms.openlocfilehash: eb5c032a020799fa19cc0a8cfaabb56e01417ff4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496706"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="df601-101">Les DateTime ContentDisposition retournent une chaîne légèrement différente</span><span class="sxs-lookup"><span data-stu-id="df601-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="df601-102">Détails</span><span class="sxs-lookup"><span data-stu-id="df601-102">Details</span></span>

<span data-ttu-id="df601-103">À compter de la version 4.6, les représentations sous forme de chaîne des <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> ont été mises à jour pour toujours représenter le composant d’heure d’une valeur <xref:System.DateTime?displayProperty=fullName> avec deux chiffres.</span><span class="sxs-lookup"><span data-stu-id="df601-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="df601-104">Ce changement a pour but de se conformer aux normes [RFC822](https://www.ietf.org/rfc/rfc0822.txt) et [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span><span class="sxs-lookup"><span data-stu-id="df601-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="df601-105"><xref:System.Net.Mime.ContentDisposition.ToString> retourne à présent une chaîne légèrement différente dans la version 4.6, lorsque l’un des éléments d’heure de la disposition est antérieur à 10:00.</span><span class="sxs-lookup"><span data-stu-id="df601-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="df601-106">Notez que les ContentDisposition sont parfois sérialisés lors de leur conversion en chaînes. Pour cette raison, les opérations <xref:System.Net.Mime.ContentDisposition.ToString>, les sérialisations et les appels GetHashCode doivent être examinés.</span><span class="sxs-lookup"><span data-stu-id="df601-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df601-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="df601-107">Suggestion</span></span>

<span data-ttu-id="df601-108">Ne vous attendez pas à ce que les représentations sous forme de chaîne des ContentDisposition issues de différentes versions du .NET Framework puissent être comparées correctement.</span><span class="sxs-lookup"><span data-stu-id="df601-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="df601-109">Reconvertissez les chaînes en ContentDisposition, si possible, avant d’effectuer une comparaison.</span><span class="sxs-lookup"><span data-stu-id="df601-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="df601-110">Name</span><span class="sxs-lookup"><span data-stu-id="df601-110">Name</span></span>    | <span data-ttu-id="df601-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="df601-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df601-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="df601-112">Scope</span></span>   |<span data-ttu-id="df601-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="df601-113">Minor</span></span>|
|<span data-ttu-id="df601-114">Version</span><span class="sxs-lookup"><span data-stu-id="df601-114">Version</span></span>|<span data-ttu-id="df601-115">4,6</span><span class="sxs-lookup"><span data-stu-id="df601-115">4.6</span></span>|
|<span data-ttu-id="df601-116">Type</span><span class="sxs-lookup"><span data-stu-id="df601-116">Type</span></span>|<span data-ttu-id="df601-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="df601-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="df601-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="df601-118">Affected APIs</span></span>

- <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType>
- <xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.Mime.ContentDisposition.ToString`
- `M:System.Net.Mime.ContentDisposition.GetHashCode`

-->
