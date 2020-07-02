---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615732"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="27f15-101">La validation de schéma XSD détecte désormais les violations de contraintes uniques si des clés composées sont utilisées et que l’une d’elles est vide</span><span class="sxs-lookup"><span data-stu-id="27f15-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

#### <a name="details"></a><span data-ttu-id="27f15-102">Détails</span><span class="sxs-lookup"><span data-stu-id="27f15-102">Details</span></span>

<span data-ttu-id="27f15-103">Les versions du .NET Framework antérieures à 4.6 contenaient un bogue qui empêchait la validation XSD de détecter les contraintes uniques des clés composées si l’une d’elles était vide.</span><span class="sxs-lookup"><span data-stu-id="27f15-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="27f15-104">Dans le .NET Framework 4.6, ce problème est résolu.</span><span class="sxs-lookup"><span data-stu-id="27f15-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="27f15-105">La validation est désormais plus précise. Toutefois, il se peut que du code XML ne soit plus validé, alors qu’il l’était dans les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="27f15-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="27f15-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="27f15-106">Suggestion</span></span>

<span data-ttu-id="27f15-107">Si une validation moins précise du .NET Framework 4.0 est nécessaire, l’application de validation peut cibler la version 4.5 (ou antérieure) du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27f15-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="27f15-108">Toutefois, quand vous reciblez vers .NET Framework 4.6, effectuez une revue du code pour vérifier que les clés composées en double (comme décrit plus haut) ne sont pas censées être validées.</span><span class="sxs-lookup"><span data-stu-id="27f15-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>

| <span data-ttu-id="27f15-109">Nom</span><span class="sxs-lookup"><span data-stu-id="27f15-109">Name</span></span>    | <span data-ttu-id="27f15-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="27f15-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27f15-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="27f15-111">Scope</span></span>   | <span data-ttu-id="27f15-112">Edge</span><span class="sxs-lookup"><span data-stu-id="27f15-112">Edge</span></span>        |
| <span data-ttu-id="27f15-113">Version</span><span class="sxs-lookup"><span data-stu-id="27f15-113">Version</span></span> | <span data-ttu-id="27f15-114">4.6</span><span class="sxs-lookup"><span data-stu-id="27f15-114">4.6</span></span>         |
| <span data-ttu-id="27f15-115">Type</span><span class="sxs-lookup"><span data-stu-id="27f15-115">Type</span></span>    | <span data-ttu-id="27f15-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="27f15-116">Retargeting</span></span> |
