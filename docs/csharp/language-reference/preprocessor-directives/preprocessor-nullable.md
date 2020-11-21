---
description: '#Nullable-référence C#'
title: '#Nullable-référence C#'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099462"
---
# <a name="nullable-c-reference"></a><span data-ttu-id="04201-103">#nullable (référence C#)</span><span class="sxs-lookup"><span data-stu-id="04201-103">#nullable (C# Reference)</span></span>

<span data-ttu-id="04201-104">La `#nullable` directive de préprocesseur définit le contexte d' *annotation Nullable* et le *contexte d’avertissement Nullable*.</span><span class="sxs-lookup"><span data-stu-id="04201-104">The `#nullable` preprocessor directive sets the *nullable annotation context* and *nullable warning context*.</span></span> <span data-ttu-id="04201-105">Cette directive contrôle si les annotations Nullable ont un effet et si des avertissements de possibilité de valeur NULL sont fournis.</span><span class="sxs-lookup"><span data-stu-id="04201-105">This directive controls whether nullable annotations have effect, and whether nullability warnings are given.</span></span> <span data-ttu-id="04201-106">Chaque contexte est *désactivé* ou *activé*.</span><span class="sxs-lookup"><span data-stu-id="04201-106">Each context is either *disabled* or *enabled*.</span></span>

<span data-ttu-id="04201-107">Les deux contextes peuvent être spécifiés au niveau du projet (en dehors du code source C#).</span><span class="sxs-lookup"><span data-stu-id="04201-107">Both contexts can be specified at the project level (outside of C# source code).</span></span> <span data-ttu-id="04201-108">La `#nullable` directive contrôle les contextes d’annotation et d’avertissement et est prioritaire sur les paramètres au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="04201-108">The `#nullable` directive controls the annotation and warning contexts and takes precedence over the project-level settings.</span></span> <span data-ttu-id="04201-109">Une directive définit le ou les contexte (s) qu’elle contrôle jusqu’à ce qu’une autre directive la remplace, ou jusqu’à la fin du fichier source.</span><span class="sxs-lookup"><span data-stu-id="04201-109">A directive sets the context(s) it controls until another directive overrides it, or until the end of the source file.</span></span>

<span data-ttu-id="04201-110">L’effet des directives est le suivant :</span><span class="sxs-lookup"><span data-stu-id="04201-110">The effect of the directives is as follows:</span></span>

- <span data-ttu-id="04201-111">`#nullable disable`: Définit l’annotation Nullable et les contextes d’avertissement sur *désactivé*.</span><span class="sxs-lookup"><span data-stu-id="04201-111">`#nullable disable`: Sets the nullable annotation and warning contexts to *disabled*.</span></span>
- <span data-ttu-id="04201-112">`#nullable enable`: Définit l’annotation Nullable et les contextes d’avertissement sur *activé*.</span><span class="sxs-lookup"><span data-stu-id="04201-112">`#nullable enable`: Sets the nullable annotation and warning contexts to *enabled*.</span></span>
- <span data-ttu-id="04201-113">`#nullable restore`: Restaure l’annotation Nullable et les contextes d’avertissement dans les paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="04201-113">`#nullable restore`: Restores the nullable annotation and warning contexts to project settings.</span></span>
- <span data-ttu-id="04201-114">`#nullable disable annotations`: Définit le contexte d’annotation Nullable sur *désactivé*.</span><span class="sxs-lookup"><span data-stu-id="04201-114">`#nullable disable annotations`: Sets the nullable annotation context to *disabled*.</span></span>
- <span data-ttu-id="04201-115">`#nullable enable annotations`: Définit le contexte d’annotation Nullable sur *activé*.</span><span class="sxs-lookup"><span data-stu-id="04201-115">`#nullable enable annotations`: Sets the nullable annotation context to *enabled*.</span></span>
- <span data-ttu-id="04201-116">`#nullable restore annotations`: Restaure le contexte d’annotation Nullable aux paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="04201-116">`#nullable restore annotations`: Restores the nullable annotation context to project settings.</span></span>
- <span data-ttu-id="04201-117">`#nullable disable warnings`: Définit le contexte d’avertissement Nullable sur *désactivé*.</span><span class="sxs-lookup"><span data-stu-id="04201-117">`#nullable disable warnings`: Sets the nullable warning context to *disabled*.</span></span>
- <span data-ttu-id="04201-118">`#nullable enable warnings`: Définit le contexte d’avertissement Nullable sur *activé*.</span><span class="sxs-lookup"><span data-stu-id="04201-118">`#nullable enable warnings`: Sets the nullable warning context to *enabled*.</span></span>
- <span data-ttu-id="04201-119">`#nullable restore warnings`: Restaure le contexte d’avertissement Nullable aux paramètres du projet.</span><span class="sxs-lookup"><span data-stu-id="04201-119">`#nullable restore warnings`: Restores the nullable warning context to project settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="04201-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04201-120">See also</span></span>

- [<span data-ttu-id="04201-121">Référence C#</span><span class="sxs-lookup"><span data-stu-id="04201-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="04201-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="04201-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="04201-123">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="04201-123">C# Preprocessor Directives</span></span>](./index.md)
