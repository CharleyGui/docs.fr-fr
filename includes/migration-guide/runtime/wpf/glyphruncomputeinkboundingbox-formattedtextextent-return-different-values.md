---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620428"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="56202-101">GlyphRun.ComputeInkBoundingBox() et FormattedText.Extent retournent des valeurs différentes à compter de .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="56202-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="56202-102">Détails</span><span class="sxs-lookup"><span data-stu-id="56202-102">Details</span></span>

<span data-ttu-id="56202-103">Des améliorations ont été apportées à <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> et à <xref:System.Windows.Media.FormattedText.Extent> dans .NET Framework 4.5 pour résoudre les problèmes où la taille des rectangles pour les glyphes qu’ils contenaient était parfois trop petite dans .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="56202-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="56202-104">Dans le .NET Framework 4.5, certains rectangles englobants sont désormais plus grands, ce qui entraîne des différences subtiles dans la disposition de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="56202-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="56202-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="56202-105">Suggestion</span></span>

<span data-ttu-id="56202-106">Notez que la taille de certains rectangles englobants de glyphes a été augmentée.</span><span class="sxs-lookup"><span data-stu-id="56202-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="56202-107">Ces modifications sont censées améliorer la présentation et les tests hitbox. Toutefois, si vous souhaitez utiliser l’ancien comportement (versions antérieures au .NET 4.5), ajoutez l’entrée suivante au fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="56202-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="56202-108">Nom</span><span class="sxs-lookup"><span data-stu-id="56202-108">Name</span></span>    | <span data-ttu-id="56202-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="56202-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="56202-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="56202-110">Scope</span></span>   |<span data-ttu-id="56202-111">Edge</span><span class="sxs-lookup"><span data-stu-id="56202-111">Edge</span></span>|
|<span data-ttu-id="56202-112">Version</span><span class="sxs-lookup"><span data-stu-id="56202-112">Version</span></span>|<span data-ttu-id="56202-113">4,5</span><span class="sxs-lookup"><span data-stu-id="56202-113">4.5</span></span>|
|<span data-ttu-id="56202-114">Type</span><span class="sxs-lookup"><span data-stu-id="56202-114">Type</span></span>|<span data-ttu-id="56202-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="56202-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56202-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="56202-116">Affected APIs</span></span>

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
