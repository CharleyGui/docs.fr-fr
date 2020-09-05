---
ms.openlocfilehash: 8dc1b4d94d01813a8124d1340b50fa78a9b157f8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496893"
---
### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="3f0f7-101">Le redimensionnement d’une grille peut se bloquer</span><span class="sxs-lookup"><span data-stu-id="3f0f7-101">Resizing a Grid can hang</span></span>

#### <a name="details"></a><span data-ttu-id="3f0f7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3f0f7-102">Details</span></span>

<span data-ttu-id="3f0f7-103">Une boucle infinie peut se produire lors de la présentation d’une <code>T:System.Windows.Controls.Grid</code> dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f0f7-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="3f0f7-104">Les définitions de ligne contiennent deux \* lignes, déclarant une MinHeight et une MaxHeight.</span><span class="sxs-lookup"><span data-stu-id="3f0f7-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="3f0f7-105">Le contenu des \* lignes ne dépasse pas le MaxHeight correspondant</span><span class="sxs-lookup"><span data-stu-id="3f0f7-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="3f0f7-106">La hauteur disponible de la grille est dépassée par le premier MinHeight (plus les autres lignes fixes ou automatiques)</span><span class="sxs-lookup"><span data-stu-id="3f0f7-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="3f0f7-107">L’application cible .NET Framework 4.7 ou adhère à l’algorithme d’allocation de 4.7 en définissant <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span><span class="sxs-lookup"><span data-stu-id="3f0f7-107">The app targets .NET Framework 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="3f0f7-108">La boucle se produit également avec plus de deux lignes, ou dans le cas analogue pour les colonnes.</span><span class="sxs-lookup"><span data-stu-id="3f0f7-108">The loop would also happen with more than two rows, or in the analogous case for columns.</span></span> <span data-ttu-id="3f0f7-109">Le problème est résolu dans .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="3f0f7-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3f0f7-110">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3f0f7-110">Suggestion</span></span>

<span data-ttu-id="3f0f7-111">Mettre à niveau vers .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="3f0f7-111">Upgrade to .NET Framework 4.7.1.</span></span>  <span data-ttu-id="3f0f7-112">Si vous n’avez pas besoin de l’algorithme d’allocation de 4.7, vous pouvez aussi utiliser le paramètre de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="3f0f7-112">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3f0f7-113">Name</span><span class="sxs-lookup"><span data-stu-id="3f0f7-113">Name</span></span>    | <span data-ttu-id="3f0f7-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="3f0f7-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3f0f7-115">Étendue</span><span class="sxs-lookup"><span data-stu-id="3f0f7-115">Scope</span></span>   |<span data-ttu-id="3f0f7-116">Edge</span><span class="sxs-lookup"><span data-stu-id="3f0f7-116">Edge</span></span>|
|<span data-ttu-id="3f0f7-117">Version</span><span class="sxs-lookup"><span data-stu-id="3f0f7-117">Version</span></span>|<span data-ttu-id="3f0f7-118">4,7</span><span class="sxs-lookup"><span data-stu-id="3f0f7-118">4.7</span></span>|
|<span data-ttu-id="3f0f7-119">Type</span><span class="sxs-lookup"><span data-stu-id="3f0f7-119">Type</span></span>|<span data-ttu-id="3f0f7-120">Runtime</span><span class="sxs-lookup"><span data-stu-id="3f0f7-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3f0f7-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="3f0f7-121">Affected APIs</span></span>

<span data-ttu-id="3f0f7-122">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="3f0f7-122">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
