---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: df05ff6caeae2fb2db6a8d7c8fec1b81774a9fa4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005390"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="f83d2-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f83d2-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="f83d2-103">Indique au compilateur de ne pas incorporer de manifeste d'application dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="f83d2-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f83d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f83d2-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="f83d2-105">Notes</span><span class="sxs-lookup"><span data-stu-id="f83d2-105">Remarks</span></span>  
 <span data-ttu-id="f83d2-106">Quand cette option est utilisée, l’application est soumise à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste de l’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f83d2-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="f83d2-107">Pour plus d’informations sur la virtualisation, consultez [Déploiement ClickOnce sur Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="f83d2-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="f83d2-108">Pour plus d’informations sur la création de manifestes, consultez [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f83d2-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83d2-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f83d2-109">See also</span></span>

- [<span data-ttu-id="f83d2-110">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f83d2-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f83d2-111">Page Application, Concepteur de projets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f83d2-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
