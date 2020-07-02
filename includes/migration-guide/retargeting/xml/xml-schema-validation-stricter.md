---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617240"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="53074-101">La validation du schéma XML est plus stricte</span><span class="sxs-lookup"><span data-stu-id="53074-101">XML schema validation is stricter</span></span>

#### <a name="details"></a><span data-ttu-id="53074-102">Détails</span><span class="sxs-lookup"><span data-stu-id="53074-102">Details</span></span>

<span data-ttu-id="53074-103">Dans .NET Framework 4.5, la validation du schéma XML est plus stricte.</span><span class="sxs-lookup"><span data-stu-id="53074-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="53074-104">Si vous utilisez xsd:anyURI pour valider un URI tel qu'un protocole mailto, la validation échoue si l'URI contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="53074-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="53074-105">Dans les versions antérieures du .NET Framework, la validation réussissait.</span><span class="sxs-lookup"><span data-stu-id="53074-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="53074-106">Le changement affecte uniquement les applications qui ciblent .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="53074-106">The change affects only applications that target the .NET Framework 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="53074-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="53074-107">Suggestion</span></span>

<span data-ttu-id="53074-108">Si une validation moins précise de .NET Framework 4.0 est nécessaire, l’application de validation peut cibler la version 4.0 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53074-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="53074-109">Toutefois, si .NET Framework 4.5 est reciblé, effectuez une revue du code pour vérifier que les URI non valides (avec des espaces) ne sont pas attendus comme valeurs d’attribut avec le type de données anyURI.</span><span class="sxs-lookup"><span data-stu-id="53074-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>

| <span data-ttu-id="53074-110">Nom</span><span class="sxs-lookup"><span data-stu-id="53074-110">Name</span></span>    | <span data-ttu-id="53074-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="53074-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="53074-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="53074-112">Scope</span></span>   | <span data-ttu-id="53074-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="53074-113">Minor</span></span>       |
| <span data-ttu-id="53074-114">Version</span><span class="sxs-lookup"><span data-stu-id="53074-114">Version</span></span> | <span data-ttu-id="53074-115">4,5</span><span class="sxs-lookup"><span data-stu-id="53074-115">4.5</span></span>         |
| <span data-ttu-id="53074-116">Type</span><span class="sxs-lookup"><span data-stu-id="53074-116">Type</span></span>    | <span data-ttu-id="53074-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="53074-117">Retargeting</span></span> |
