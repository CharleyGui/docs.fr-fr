---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620503"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="045d3-101">XmlSchemaException définit désormais les positions de ligne correctement</span><span class="sxs-lookup"><span data-stu-id="045d3-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="045d3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="045d3-102">Details</span></span>

<span data-ttu-id="045d3-103">Si la valeur <xref:System.Xml.Linq.LoadOptions.SetLineInfo> est passée à la méthode Load et qu’une erreur de validation se produit, les propriétés <xref:System.Xml.Schema.XmlSchemaException.LineNumber> et <xref:System.Xml.Schema.XmlSchemaException.LinePosition> contiennent désormais les informations de ligne.</span><span class="sxs-lookup"><span data-stu-id="045d3-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="045d3-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="045d3-104">Suggestion</span></span>

<span data-ttu-id="045d3-105">Le code de gestion des exceptions qui suppose que <xref:System.Xml.Schema.XmlSchemaException.LineNumber> et <xref:System.Xml.Schema.XmlSchemaException.LinePosition> ne seront pas définies doit être modifié, car ces propriétés seront maintenant définies correctement quand SetLineInfo est utilisé lors du chargement du code XML.</span><span class="sxs-lookup"><span data-stu-id="045d3-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="045d3-106">Nom</span><span class="sxs-lookup"><span data-stu-id="045d3-106">Name</span></span>    | <span data-ttu-id="045d3-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="045d3-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="045d3-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="045d3-108">Scope</span></span>   |<span data-ttu-id="045d3-109">Edge</span><span class="sxs-lookup"><span data-stu-id="045d3-109">Edge</span></span>|
|<span data-ttu-id="045d3-110">Version</span><span class="sxs-lookup"><span data-stu-id="045d3-110">Version</span></span>|<span data-ttu-id="045d3-111">4,5</span><span class="sxs-lookup"><span data-stu-id="045d3-111">4.5</span></span>|
|<span data-ttu-id="045d3-112">Type</span><span class="sxs-lookup"><span data-stu-id="045d3-112">Type</span></span>|<span data-ttu-id="045d3-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="045d3-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="045d3-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="045d3-114">Affected APIs</span></span>

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
