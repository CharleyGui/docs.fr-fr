---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615719"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a><span data-ttu-id="5b7e2-101">L’arrondi des marges dans la disposition WPF a changé</span><span class="sxs-lookup"><span data-stu-id="5b7e2-101">WPF layout rounding of margins has changed</span></span>

#### <a name="details"></a><span data-ttu-id="5b7e2-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5b7e2-102">Details</span></span>

<span data-ttu-id="5b7e2-103">La façon dont les marges sont arrondies, les bordures et l'arrière-plan ont changé.</span><span class="sxs-lookup"><span data-stu-id="5b7e2-103">The way in which margins are rounded and borders and the background inside of them has changed.</span></span> <span data-ttu-id="5b7e2-104">Résultat de cette modification :</span><span class="sxs-lookup"><span data-stu-id="5b7e2-104">As a result of this change:</span></span>

- <span data-ttu-id="5b7e2-105">La largeur ou la hauteur d'éléments peut croître ou diminuer d'un pixel au plus.</span><span class="sxs-lookup"><span data-stu-id="5b7e2-105">The width or height of elements may grow or shrink by at most one pixel.</span></span>
- <span data-ttu-id="5b7e2-106">La position d'un objet peut se déplacer d'un pixel au plus.</span><span class="sxs-lookup"><span data-stu-id="5b7e2-106">The placement of an object can move by at most one pixel.</span></span>
- <span data-ttu-id="5b7e2-107">Les éléments centrés peuvent être décalés verticalement ou horizontalement d'un pixel au plus.</span><span class="sxs-lookup"><span data-stu-id="5b7e2-107">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>
<span data-ttu-id="5b7e2-108">Par défaut, cette nouvelle disposition est activée uniquement pour les applications qui ciblent le .NET. Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="5b7e2-108">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5b7e2-109">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5b7e2-109">Suggestion</span></span>

<span data-ttu-id="5b7e2-110">Dans la mesure où cette modification tend à éliminer le découpage droit ou inférieur des contrôles WPF dont le PPP est élevé, les applications qui ciblent les versions antérieures du .NET Framework, mais qui s'exécutent sur le .NET Framework 4.6, peuvent choisir ce nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="5b7e2-110">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

<span data-ttu-id="5b7e2-111">Les applications qui ciblent .NET Framework 4.6, mais veulent que les contrôles WPF soient rendus à l’aide de l’algorithme de disposition précédent peuvent y parvenir en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="5b7e2-111">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| <span data-ttu-id="5b7e2-112">Nom</span><span class="sxs-lookup"><span data-stu-id="5b7e2-112">Name</span></span>    | <span data-ttu-id="5b7e2-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="5b7e2-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5b7e2-114">Étendue</span><span class="sxs-lookup"><span data-stu-id="5b7e2-114">Scope</span></span>   | <span data-ttu-id="5b7e2-115">Secondaire</span><span class="sxs-lookup"><span data-stu-id="5b7e2-115">Minor</span></span>       |
| <span data-ttu-id="5b7e2-116">Version</span><span class="sxs-lookup"><span data-stu-id="5b7e2-116">Version</span></span> | <span data-ttu-id="5b7e2-117">4.6</span><span class="sxs-lookup"><span data-stu-id="5b7e2-117">4.6</span></span>         |
| <span data-ttu-id="5b7e2-118">Type</span><span class="sxs-lookup"><span data-stu-id="5b7e2-118">Type</span></span>    | <span data-ttu-id="5b7e2-119">Reciblage</span><span class="sxs-lookup"><span data-stu-id="5b7e2-119">Retargeting</span></span> |
