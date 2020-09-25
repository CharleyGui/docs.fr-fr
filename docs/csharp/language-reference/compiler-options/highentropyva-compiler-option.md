---
description: -highentropyva (Options du compilateur C#)
title: -highentropyva (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: f3cdeb5e63d632fecbbd94501558cc53c28a918a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173202"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="f1181-103">-highentropyva (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f1181-103">-highentropyva (C# Compiler Options)</span></span>

<span data-ttu-id="f1181-104">L’option du compilateur **-highentropyva** indique au noyau Windows si un fichier exécutable particulier prend en charge la randomisation du format d’espace d’adresse (ASLR) de forte entropie.</span><span class="sxs-lookup"><span data-stu-id="f1181-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1181-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1181-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f1181-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1181-106">Arguments</span></span>  

 <span data-ttu-id="f1181-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f1181-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="f1181-108">Cette option spécifie qu’un exécutable 64 bits ou un exécutable marqué par l’option du compilateur [-platform:anycpu](./platform-compiler-option.md) prend en charge un espace d’adressage virtuel d’entropie élevée.</span><span class="sxs-lookup"><span data-stu-id="f1181-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="f1181-109">Cette option est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="f1181-109">The option is disabled by default.</span></span> <span data-ttu-id="f1181-110">Utilisez **-highentropyva+** ou **-highentropyva** pour l’activer.</span><span class="sxs-lookup"><span data-stu-id="f1181-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1181-111">Notes</span><span class="sxs-lookup"><span data-stu-id="f1181-111">Remarks</span></span>  

 <span data-ttu-id="f1181-112">L’option **-highentropyva** permet à des versions compatibles du noyau Windows d’utiliser un degré d’entropie plus élevé lors de la randomisation du format de l’espace d’adresse d’un processus.</span><span class="sxs-lookup"><span data-stu-id="f1181-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="f1181-113">En utilisant un degré d’entropie plus élevé, vous pouvez allouer un plus grand nombre d’adresses aux zones de mémoire, telles que les piles et les tas.</span><span class="sxs-lookup"><span data-stu-id="f1181-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="f1181-114">Par conséquent, il est plus difficile de deviner l’emplacement d’une zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f1181-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="f1181-115">Quand l’option du compilateur **-highentropyva** est spécifiée, l’exécutable cible et tous les modules dont il dépend doivent être capables de gérer les valeurs de pointeur supérieures à 4 Go lorsqu’ils sont exécutés en tant que processus 64 bits.</span><span class="sxs-lookup"><span data-stu-id="f1181-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
