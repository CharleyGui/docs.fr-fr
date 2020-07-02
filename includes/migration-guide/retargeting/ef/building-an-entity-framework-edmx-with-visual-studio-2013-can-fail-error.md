---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615690"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a><span data-ttu-id="f3ec3-101">La génération d’un fichier edmx Entity Framework avec Visual Studio 2013 peut échouer avec l’erreur MSB4062 si vous utilisez les tâches EntityDeploySplit ou EntityClean</span><span class="sxs-lookup"><span data-stu-id="f3ec3-101">Building an Entity Framework edmx with Visual Studio 2013 can fail with error MSB4062 if using the EntityDeploySplit or EntityClean tasks</span></span>

#### <a name="details"></a><span data-ttu-id="f3ec3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f3ec3-102">Details</span></span>

<span data-ttu-id="f3ec3-103">L’emplacement des fichiers des outils MSBuild 12.0 (inclus dans Visual Studio 2013) a changé, ce qui rend les anciens fichiers de cibles Entity Framework non valides.</span><span class="sxs-lookup"><span data-stu-id="f3ec3-103">MSBuild 12.0 tools (included in Visual Studio 2013) changed MSBuild file locations, causing older Entity Framework targets files to be invalid.</span></span> <span data-ttu-id="f3ec3-104">Les tâches `EntityDeploySplit` et `EntityClean` échouent, car elles ne parviennent pas à trouver `Microsoft.Data.Entity.Build.Tasks.dll`.</span><span class="sxs-lookup"><span data-stu-id="f3ec3-104">The result is that `EntityDeploySplit` and `EntityClean` tasks fail because they are unable to find `Microsoft.Data.Entity.Build.Tasks.dll`.</span></span> <span data-ttu-id="f3ec3-105">Notez que ce problème est dû à un changement d’ensemble d’outils (MSBuild/VS), et non à un changement du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3ec3-105">Note that this break is because of a toolset (MSBuild/VS) change, not because of a .NET Framework change.</span></span> <span data-ttu-id="f3ec3-106">Il est dû à la mise à niveau des outils de développement, et non à celle du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3ec3-106">It will only occur when upgrading developer tools, not when merely upgrading the .NET Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f3ec3-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f3ec3-107">Suggestion</span></span>

<span data-ttu-id="f3ec3-108">Les fichiers de cibles Entity Framework ont été corrigés pour fonctionner avec la nouvelle disposition MSBuild de .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="f3ec3-108">Entity Framework targets files are fixed to work with the new MSBuild layout beginning in the .NET Framework 4.6.</span></span> <span data-ttu-id="f3ec3-109">Vous pouvez résoudre ce problème en mettant à niveau votre .NET Framework vers la version 4.6.</span><span class="sxs-lookup"><span data-stu-id="f3ec3-109">Upgrading to that version of the Framework will fix this issue.</span></span> <span data-ttu-id="f3ec3-110">Vous pouvez également appliquer [cette solution de contournement](https://stackoverflow.com/a/24249247/131944) pour corriger directement les fichiers de cibles.</span><span class="sxs-lookup"><span data-stu-id="f3ec3-110">Alternatively, [this workaround](https://stackoverflow.com/a/24249247/131944) can be used to patch the targets files directly.</span></span>

| <span data-ttu-id="f3ec3-111">Nom</span><span class="sxs-lookup"><span data-stu-id="f3ec3-111">Name</span></span>    | <span data-ttu-id="f3ec3-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="f3ec3-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f3ec3-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="f3ec3-113">Scope</span></span>   | <span data-ttu-id="f3ec3-114">Majeure</span><span class="sxs-lookup"><span data-stu-id="f3ec3-114">Major</span></span>       |
| <span data-ttu-id="f3ec3-115">Version</span><span class="sxs-lookup"><span data-stu-id="f3ec3-115">Version</span></span> | <span data-ttu-id="f3ec3-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f3ec3-116">4.5.1</span></span>       |
| <span data-ttu-id="f3ec3-117">Type</span><span class="sxs-lookup"><span data-stu-id="f3ec3-117">Type</span></span>    | <span data-ttu-id="f3ec3-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="f3ec3-118">Retargeting</span></span> |
