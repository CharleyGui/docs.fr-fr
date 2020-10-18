---
title: Les instructions 'Module' ne peuvent intervenir qu'au niveau du fichier ou de l'espace de noms
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: b946a527d3de3a030ac03691c77afcf440f518ee
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160312"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="2b3be-102">BC30617 : les instructions’module’ne peuvent se produire qu’au niveau du fichier ou de l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="2b3be-102">BC30617: 'Module' statements can occur only at file or namespace level</span></span>

<span data-ttu-id="2b3be-103">`Module` les instructions doivent apparaître en haut de votre fichier source immédiatement après `Option` et `Imports` les instructions, les attributs globaux et les déclarations d’espaces de noms, mais avant toutes les autres déclarations.</span><span class="sxs-lookup"><span data-stu-id="2b3be-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>

 <span data-ttu-id="2b3be-104">**ID d’erreur :** BC30617</span><span class="sxs-lookup"><span data-stu-id="2b3be-104">**Error ID:** BC30617</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2b3be-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2b3be-105">To correct this error</span></span>

- <span data-ttu-id="2b3be-106">Déplacez l’instruction `Module` en haut de votre déclaration d’espace de noms ou de votre fichier source.</span><span class="sxs-lookup"><span data-stu-id="2b3be-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b3be-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b3be-107">See also</span></span>

- [<span data-ttu-id="2b3be-108">Module, instruction</span><span class="sxs-lookup"><span data-stu-id="2b3be-108">Module Statement</span></span>](../statements/module-statement.md)
