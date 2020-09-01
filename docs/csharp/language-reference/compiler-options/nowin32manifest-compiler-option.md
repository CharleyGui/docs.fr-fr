---
description: -nowin32manifest (Options du compilateur C#)
title: -nowin32manifest (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8514ab5b118e320d456d1b7367fab3b463c3607a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125057"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="97b1e-103">-nowin32manifest (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="97b1e-103">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="97b1e-104">Utilisez l’option **-nowin32manifest** pour indiquer au compilateur de ne pas incorporer le manifeste de l’application dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="97b1e-104">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97b1e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97b1e-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="97b1e-106">Notes</span><span class="sxs-lookup"><span data-stu-id="97b1e-106">Remarks</span></span>  
 <span data-ttu-id="97b1e-107">Quand cette option est utilisée, l’application est soumise à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste de l’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="97b1e-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="97b1e-108">Dans Visual Studio, définissez cette option dans la page de propriétés **Application** en sélectionnant l’option **Créer une application sans fichier manifeste** dans la zone de liste déroulante **Manifeste**.</span><span class="sxs-lookup"><span data-stu-id="97b1e-108">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="97b1e-109">Pour plus d’informations, consultez [page application, concepteur de projets (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="97b1e-109">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="97b1e-110">Pour plus d’informations sur la création d’un manifeste, consultez [-win32manifest (options du compilateur C#)](./win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="97b1e-110">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b1e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97b1e-111">See also</span></span>

- [<span data-ttu-id="97b1e-112">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="97b1e-112">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="97b1e-113">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="97b1e-113">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
