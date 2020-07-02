---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621080"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="4d8dc-101">Modifications avec rupture pour SignedXml et EncryptedXml</span><span class="sxs-lookup"><span data-stu-id="4d8dc-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="4d8dc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4d8dc-102">Details</span></span>

<span data-ttu-id="4d8dc-103">Dans .NET Framework 4.6.2, les correctifs de sécurité dans <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> et <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> aboutissent à différents comportements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4d8dc-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="4d8dc-104">Par exemple,</span><span class="sxs-lookup"><span data-stu-id="4d8dc-104">For example,</span></span><ul><li><span data-ttu-id="4d8dc-105">Si un document contient plusieurs éléments avec le même attribut <code>id</code> et qu’une signature cible l’un de ces éléments comme racine de la signature, le document est désormais considéré comme non valide.</span><span class="sxs-lookup"><span data-stu-id="4d8dc-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="4d8dc-106">Les documents utilisant des algorithmes de transformation XPath non canoniques dans les références sont désormais considérés comme non valides.</span><span class="sxs-lookup"><span data-stu-id="4d8dc-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="4d8dc-107">Les documents utilisant des algorithmes de transformation XSLT non canoniques dans les références sont désormais considérés comme non valides.</span><span class="sxs-lookup"><span data-stu-id="4d8dc-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="4d8dc-108">N’importe quel programme tirant parti des signatures détachées des ressources externes ne pourra plus le faire.</span><span class="sxs-lookup"><span data-stu-id="4d8dc-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="4d8dc-109">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4d8dc-109">Suggestion</span></span>

<span data-ttu-id="4d8dc-110">Les développeurs peuvent examiner l’utilisation de <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> et <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, ainsi que les types dérivés de <xref:System.Security.Cryptography.Xml.Transform>, car un destinataire du document risque de ne pas pouvoir le traiter.</span><span class="sxs-lookup"><span data-stu-id="4d8dc-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="4d8dc-111">Nom</span><span class="sxs-lookup"><span data-stu-id="4d8dc-111">Name</span></span>    | <span data-ttu-id="4d8dc-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="4d8dc-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4d8dc-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="4d8dc-113">Scope</span></span>   |<span data-ttu-id="4d8dc-114">Secondaire</span><span class="sxs-lookup"><span data-stu-id="4d8dc-114">Minor</span></span>|
|<span data-ttu-id="4d8dc-115">Version</span><span class="sxs-lookup"><span data-stu-id="4d8dc-115">Version</span></span>|<span data-ttu-id="4d8dc-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="4d8dc-116">4.6.2</span></span>|
|<span data-ttu-id="4d8dc-117">Type</span><span class="sxs-lookup"><span data-stu-id="4d8dc-117">Type</span></span>|<span data-ttu-id="4d8dc-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="4d8dc-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4d8dc-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="4d8dc-119">Affected APIs</span></span>

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
