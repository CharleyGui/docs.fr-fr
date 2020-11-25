---
title: 'Modification avec rupture : modification du comportement de PublishDepsFilePath'
description: Découvrez la modification avec rupture dans .NET 5,0 où la propriété MSBuild PublishDepsFilePath est vide pour les applications à fichier unique.
ms.date: 09/17/2020
ms.openlocfilehash: 70631beff31aa3388e59f3b79875ef437351451a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761316"
---
# <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="a51cd-103">Changement de comportement de PublishDepsFilePath</span><span class="sxs-lookup"><span data-stu-id="a51cd-103">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="a51cd-104">La `PublishDepsFilePath` propriété MSBuild est vide pour les applications à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="a51cd-104">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="a51cd-105">En outre, pour les applications qui ne comportent qu’un seul fichier, le *deps.jssur* le fichier peut ne pas être copié dans le répertoire de sortie jusqu’à la version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a51cd-105">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a51cd-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a51cd-106">Version introduced</span></span>

<span data-ttu-id="a51cd-107">5.0</span><span class="sxs-lookup"><span data-stu-id="a51cd-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="a51cd-108">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="a51cd-108">Change description</span></span>

<span data-ttu-id="a51cd-109">Dans les versions précédentes de .NET, la `PublishDepsFilePath` propriété MSBuild est le chemin d’accès à l'deps.jsde l’application *sur* le fichier dans le répertoire de sortie pour les applications à fichier unique, et un chemin d’accès dans le répertoire intermédiaire pour les applications à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="a51cd-109">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="a51cd-110">À compter de .NET 5,0, `PublishDepsFilePath` est vide pour les applications à fichier unique et une nouvelle `IntermediateDepsFilePath` propriété spécifie le *deps.jsà* l’emplacement dans le répertoire intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="a51cd-110">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="a51cd-111">En outre, pour les applications qui ne comportent qu’un seul fichier, le *deps.jssur* le fichier peut ne pas être copié dans le répertoire de sortie (autrement dit, le chemin d’accès spécifié par `PublishDepsFilePath` ) jusqu’à la version ultérieure de la Build.</span><span class="sxs-lookup"><span data-stu-id="a51cd-111">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a51cd-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a51cd-112">Reason for change</span></span>

<span data-ttu-id="a51cd-113">Cette modification a été effectuée pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="a51cd-113">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="a51cd-114">En raison de la refactorisation de la logique de publication afin de prendre en charge des [applications à fichier unique améliorées](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) dans .net 5.</span><span class="sxs-lookup"><span data-stu-id="a51cd-114">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="a51cd-115">Dans les applications à fichier unique, pour vous aider à vous prémunir des cibles qui essaient de réécrire le *deps.jssur* le fichier une fois que *deps.jssur* a déjà été regroupé, sans aucun impact sur l’application.</span><span class="sxs-lookup"><span data-stu-id="a51cd-115">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="a51cd-116">Pour cette raison, `PublishDepsFilePath` est vide pour les applications à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="a51cd-116">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a51cd-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a51cd-117">Recommended action</span></span>

<span data-ttu-id="a51cd-118">Les cibles qui réécrivent le *deps.jssur* le fichier doivent généralement le faire à l’aide de la `IntermediateDepsFilePath` propriété.</span><span class="sxs-lookup"><span data-stu-id="a51cd-118">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a51cd-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="a51cd-119">Affected APIs</span></span>

<span data-ttu-id="a51cd-120">N/A</span><span class="sxs-lookup"><span data-stu-id="a51cd-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
