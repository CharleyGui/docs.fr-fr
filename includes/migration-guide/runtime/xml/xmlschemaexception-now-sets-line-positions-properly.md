---
ms.openlocfilehash: 04d1c1162dc79bbcb0578c6661466f4d58a57acc
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496564"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="19f85-101">XmlSchemaException définit désormais les positions de ligne correctement</span><span class="sxs-lookup"><span data-stu-id="19f85-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="19f85-102">Détails</span><span class="sxs-lookup"><span data-stu-id="19f85-102">Details</span></span>

<span data-ttu-id="19f85-103">Si la valeur <xref:System.Xml.Linq.LoadOptions.SetLineInfo> est passée à la méthode Load et qu’une erreur de validation se produit, les propriétés <xref:System.Xml.Schema.XmlSchemaException.LineNumber> et <xref:System.Xml.Schema.XmlSchemaException.LinePosition> contiennent désormais les informations de ligne.</span><span class="sxs-lookup"><span data-stu-id="19f85-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="19f85-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="19f85-104">Suggestion</span></span>

<span data-ttu-id="19f85-105">Le code de gestion des exceptions qui suppose que <xref:System.Xml.Schema.XmlSchemaException.LineNumber> et <xref:System.Xml.Schema.XmlSchemaException.LinePosition> ne seront pas définies doit être modifié, car ces propriétés seront maintenant définies correctement quand SetLineInfo est utilisé lors du chargement du code XML.</span><span class="sxs-lookup"><span data-stu-id="19f85-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="19f85-106">Name</span><span class="sxs-lookup"><span data-stu-id="19f85-106">Name</span></span>    | <span data-ttu-id="19f85-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="19f85-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="19f85-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="19f85-108">Scope</span></span>   |<span data-ttu-id="19f85-109">Edge</span><span class="sxs-lookup"><span data-stu-id="19f85-109">Edge</span></span>|
|<span data-ttu-id="19f85-110">Version</span><span class="sxs-lookup"><span data-stu-id="19f85-110">Version</span></span>|<span data-ttu-id="19f85-111">4,5</span><span class="sxs-lookup"><span data-stu-id="19f85-111">4.5</span></span>|
|<span data-ttu-id="19f85-112">Type</span><span class="sxs-lookup"><span data-stu-id="19f85-112">Type</span></span>|<span data-ttu-id="19f85-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="19f85-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="19f85-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="19f85-114">Affected APIs</span></span>

- <xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Xml.Linq.LoadOptions.SetLineInfo`

-->
