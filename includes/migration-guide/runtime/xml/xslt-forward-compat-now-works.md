---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620515"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="b62fe-101">La compatibilité ascendante de XSLT fonctionne désormais</span><span class="sxs-lookup"><span data-stu-id="b62fe-101">XSLT forward compat now works</span></span>

#### <a name="details"></a><span data-ttu-id="b62fe-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b62fe-102">Details</span></span>

<span data-ttu-id="b62fe-103">Dans .NET Framework 4, la compatibilité ascendante de XSLT 1.0 avait les problèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="b62fe-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="b62fe-104">Le chargement d'une feuille de style échouait si sa version avait la valeur 2.0 et si l'analyseur rencontrait une construction XSLT 1.0 non reconnue.</span><span class="sxs-lookup"><span data-stu-id="b62fe-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="b62fe-105">La construction <code>xsl:sort</code> ne pouvait pas trier les données si la version de la feuille de style était définie sur 1.1.</span><span class="sxs-lookup"><span data-stu-id="b62fe-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="b62fe-106">Dans le .NET Framework 4.5, ces problèmes ont été résolus et le mode de compatibilité ascendante de XSLT 1.0 fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="b62fe-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b62fe-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b62fe-107">Suggestion</span></span>

<span data-ttu-id="b62fe-108">La plupart des applications ne devraient pas être affectées, mais les données sont triées différemment dans certains cas maintenant que xsl:sort est respecté.</span><span class="sxs-lookup"><span data-stu-id="b62fe-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="b62fe-109">Si <code>xsl:sort</code> est utilisé dans des feuilles de style 1.1, vérifiez que les applications ne dépendaient pas de l’ordre non trié des données.</span><span class="sxs-lookup"><span data-stu-id="b62fe-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="b62fe-110">Si des applications s’appuient sur le comportement de tri de la version 4.0, supprimez <code>xsl:sort</code> de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="b62fe-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>

| <span data-ttu-id="b62fe-111">Nom</span><span class="sxs-lookup"><span data-stu-id="b62fe-111">Name</span></span>    | <span data-ttu-id="b62fe-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="b62fe-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b62fe-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="b62fe-113">Scope</span></span>   |<span data-ttu-id="b62fe-114">Edge</span><span class="sxs-lookup"><span data-stu-id="b62fe-114">Edge</span></span>|
|<span data-ttu-id="b62fe-115">Version</span><span class="sxs-lookup"><span data-stu-id="b62fe-115">Version</span></span>|<span data-ttu-id="b62fe-116">4,5</span><span class="sxs-lookup"><span data-stu-id="b62fe-116">4.5</span></span>|
|<span data-ttu-id="b62fe-117">Type</span><span class="sxs-lookup"><span data-stu-id="b62fe-117">Type</span></span>|<span data-ttu-id="b62fe-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="b62fe-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b62fe-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="b62fe-119">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
