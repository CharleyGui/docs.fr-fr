---
title: 'NETSDK1022 : des éléments en double ont été inclus.'
description: Comment résoudre le message d’élément en double basé sur les includes par défaut.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: 46c3d7d451e7c9e5b456b6e4e45054c3a4844386
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445785"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="8e6ab-103">NETSDK1022 : des éléments en double ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="8e6ab-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="8e6ab-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .NET 2.1.100 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8e6ab-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="8e6ab-105">À compter de Visual Studio 15,3, le kit de développement logiciel (SDK) .NET comprend automatiquement les éléments du répertoire du projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="8e6ab-105">Starting in Visual Studio 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="8e6ab-106">Cela comprend `Compile` les `Content` cibles et.</span><span class="sxs-lookup"><span data-stu-id="8e6ab-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="8e6ab-107">Cela doit vraiment nettoyer votre fichier projet et réduire la complexité que vous y avez.</span><span class="sxs-lookup"><span data-stu-id="8e6ab-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="8e6ab-108">Vous pouvez rétablir le comportement antérieur en affectant à la propriété correcte la valeur false.</span><span class="sxs-lookup"><span data-stu-id="8e6ab-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="8e6ab-109">Exemple pour les `Compile` éléments :</span><span class="sxs-lookup"><span data-stu-id="8e6ab-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
