---
ms.openlocfilehash: f87b70708398226516ab5eac32c24a9fc2c1106b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615733"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a><span data-ttu-id="81f06-101">XmlWriter lève des paires de substitution non valides</span><span class="sxs-lookup"><span data-stu-id="81f06-101">XmlWriter throws on invalid surrogate pairs</span></span>

#### <a name="details"></a><span data-ttu-id="81f06-102">Détails</span><span class="sxs-lookup"><span data-stu-id="81f06-102">Details</span></span>

<span data-ttu-id="81f06-103">Pour les applications qui ciblent .NET Framework 4.5.2 ou les versions antérieures, l’écriture d’une paire de substitution non valide à l’aide de la gestion des exceptions de secours ne lève pas toujours une exception.</span><span class="sxs-lookup"><span data-stu-id="81f06-103">For apps that target the .NET Framework 4.5.2 or previous versions, writing an invalid surrogate pair using exception fallback handling does not always throw an exception.</span></span> <span data-ttu-id="81f06-104">Pour les applications qui ciblent .NET Framework 4.6, toute tentative d’écriture d’une paire de substitution non valide lève une <xref:System.ArgumentException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="81f06-104">For apps that target the .NET Framework 4.6, attempting to write an invalid surrogate pair throws an <xref:System.ArgumentException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="81f06-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="81f06-105">Suggestion</span></span>

<span data-ttu-id="81f06-106">Si nécessaire, vous pouvez éviter cette interruption en ciblant le .NET Framework 4.5.2 ou antérieur.</span><span class="sxs-lookup"><span data-stu-id="81f06-106">If necessary, this break can be avoided by targeting the .NET Framework 4.5.2 or earlier.</span></span> <span data-ttu-id="81f06-107">Vous pouvez également prétraiter les paires de substitution non valides en code XML valide avant de les écrire.</span><span class="sxs-lookup"><span data-stu-id="81f06-107">Alternatively, invalid surrogate pairs can be pre-processed into valid xml prior to writing them.</span></span>

| <span data-ttu-id="81f06-108">Nom</span><span class="sxs-lookup"><span data-stu-id="81f06-108">Name</span></span>    | <span data-ttu-id="81f06-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="81f06-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="81f06-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="81f06-110">Scope</span></span>   | <span data-ttu-id="81f06-111">Edge</span><span class="sxs-lookup"><span data-stu-id="81f06-111">Edge</span></span>        |
| <span data-ttu-id="81f06-112">Version</span><span class="sxs-lookup"><span data-stu-id="81f06-112">Version</span></span> | <span data-ttu-id="81f06-113">4.6</span><span class="sxs-lookup"><span data-stu-id="81f06-113">4.6</span></span>         |
| <span data-ttu-id="81f06-114">Type</span><span class="sxs-lookup"><span data-stu-id="81f06-114">Type</span></span>    | <span data-ttu-id="81f06-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="81f06-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="81f06-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="81f06-116">Affected APIs</span></span>

- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType>
