---
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: 9e5ad874431028faf17333a9bbd7e9356ef22d55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347888"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="a85ad-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a85ad-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="a85ad-103">Indique au compilateur de ne pas incorporer de manifeste d'application dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="a85ad-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a85ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a85ad-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="a85ad-105">Notes</span><span class="sxs-lookup"><span data-stu-id="a85ad-105">Remarks</span></span>  
 <span data-ttu-id="a85ad-106">Quand cette option est utilisée, l’application est soumise à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste de l’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a85ad-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="a85ad-107">Pour plus d’informations sur la virtualisation, consultez [Déploiement ClickOnce sur Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="a85ad-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="a85ad-108">Pour plus d’informations sur la création de manifestes, consultez [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="a85ad-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85ad-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a85ad-109">See also</span></span>

- [<span data-ttu-id="a85ad-110">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a85ad-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a85ad-111">Page Application, Concepteur de projet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a85ad-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
