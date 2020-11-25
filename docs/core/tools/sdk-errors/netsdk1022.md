---
title: 'NETSDK1022 : des éléments en double ont été inclus.'
description: Comment résoudre le message d’élément en double basé sur les includes par défaut.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: c2bdbbb5503e5e4f6e6826f95f5a2cb08c908ceb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717866"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="bfb5b-103">NETSDK1022 : des éléments en double ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="bfb5b-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bfb5b-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="bfb5b-105">À compter de Visual Studio 2017/MSBuild version 15,3, le kit de développement logiciel (SDK) .NET comprend automatiquement les éléments du répertoire du projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-105">Starting in Visual Studio 2017 / MSBuild version 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="bfb5b-106">Cela comprend `Compile` les `Content` cibles et.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="bfb5b-107">Cela doit vraiment nettoyer votre fichier projet et réduire la complexité que vous y avez.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="bfb5b-108">Vous pouvez rétablir le comportement antérieur en affectant à la propriété correcte la valeur false.</span><span class="sxs-lookup"><span data-stu-id="bfb5b-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="bfb5b-109">Exemple pour les `Compile` éléments :</span><span class="sxs-lookup"><span data-stu-id="bfb5b-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
