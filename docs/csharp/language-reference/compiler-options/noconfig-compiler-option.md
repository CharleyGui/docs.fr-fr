---
description: -noconfig (Options du compilateur C#)
title: -noconfig (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 677b96df8c6686e46c0db93eabe72dd483b947e4
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466064"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="00f46-103">-noconfig (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="00f46-103">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="00f46-104">L’option **-noconfig** indique au compilateur de ne pas compiler avec le fichier csc. rsp, qui se trouve dans le même répertoire que le fichier csc.exe et est chargé à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="00f46-104">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f46-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00f46-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="00f46-106">Notes</span><span class="sxs-lookup"><span data-stu-id="00f46-106">Remarks</span></span>  
 <span data-ttu-id="00f46-107">Le fichier csc. rsp fait référence à tous les assemblys fournis avec .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00f46-107">The csc.rsp file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="00f46-108">Les références réelles qui sont incluses dans l’environnement de développement Visual Studio .NET varient en fonction du type de projet.</span><span class="sxs-lookup"><span data-stu-id="00f46-108">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="00f46-109">Vous pouvez modifier le fichier csc. RSP et spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation à partir de la ligne de commande avec csc.exe (à l’exception de l’option **-noconfig** ).</span><span class="sxs-lookup"><span data-stu-id="00f46-109">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="00f46-110">Le compilateur traite les options passées à la commande **csc** en dernier.</span><span class="sxs-lookup"><span data-stu-id="00f46-110">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="00f46-111">De ce fait, toute option sur la ligne de commande se substitue au paramètre de la même option dans le fichier csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="00f46-111">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="00f46-112">Si vous ne souhaitez pas que le compilateur recherche et utilise les paramètres dans le fichier csc. rsp, spécifiez **-noconfig**.</span><span class="sxs-lookup"><span data-stu-id="00f46-112">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="00f46-113">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="00f46-113">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f46-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00f46-114">See also</span></span>

- [<span data-ttu-id="00f46-115">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="00f46-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="00f46-116">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="00f46-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
