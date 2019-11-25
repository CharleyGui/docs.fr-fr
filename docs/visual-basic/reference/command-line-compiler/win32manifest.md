---
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cef1e6c19e7fdd6fc9f42c8fc36008314ea80a80
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349130"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="7efef-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7efef-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="7efef-103">Identifie un fichier manifeste d'application Win32 défini par l'utilisateur à incorporer dans le fichier exécutable portable (PE) d'un projet.</span><span class="sxs-lookup"><span data-stu-id="7efef-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7efef-104">Syntax</span></span>  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="7efef-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7efef-105">Arguments</span></span>  
  
|<span data-ttu-id="7efef-106">Terme</span><span class="sxs-lookup"><span data-stu-id="7efef-106">Term</span></span>|<span data-ttu-id="7efef-107">Définition</span><span class="sxs-lookup"><span data-stu-id="7efef-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="7efef-108">The path of the custom manifest file.</span><span class="sxs-lookup"><span data-stu-id="7efef-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7efef-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7efef-109">Remarks</span></span>  
 <span data-ttu-id="7efef-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span><span class="sxs-lookup"><span data-stu-id="7efef-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="7efef-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7efef-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="7efef-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span><span class="sxs-lookup"><span data-stu-id="7efef-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7efef-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span><span class="sxs-lookup"><span data-stu-id="7efef-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="7efef-114">If you try to use both options in the same command line, you will get a build error.</span><span class="sxs-lookup"><span data-stu-id="7efef-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="7efef-115">Une application sans manifeste d’application pour spécifier le niveau d’exécution requis est soumise à une virtualisation des fichiers/registres sous la fonctionnalité de contrôle de compte d’utilisateur de Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="7efef-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="7efef-116">Pour plus d’informations sur la virtualisation, consultez [Déploiement ClickOnce sur Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="7efef-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="7efef-117">Your application will be subject to virtualization if either of the following conditions is true:</span><span class="sxs-lookup"><span data-stu-id="7efef-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="7efef-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span><span class="sxs-lookup"><span data-stu-id="7efef-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="7efef-119">Vous fournissez un manifeste personnalisé qui ne spécifie pas le niveau d’exécution requis.</span><span class="sxs-lookup"><span data-stu-id="7efef-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="7efef-120">Visual Studio crée un fichier .manifest par défaut et le stocke dans les répertoires de débogage et de mise en production avec le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="7efef-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="7efef-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span><span class="sxs-lookup"><span data-stu-id="7efef-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="7efef-122">Pour plus d’informations, consultez [Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7efef-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="7efef-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span><span class="sxs-lookup"><span data-stu-id="7efef-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="7efef-124">Utilisez cette même option pour que votre application soit soumise à la virtualisation des fichiers ou des registres dans Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="7efef-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="7efef-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span><span class="sxs-lookup"><span data-stu-id="7efef-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7efef-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="7efef-126">Example</span></span>  
 <span data-ttu-id="7efef-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span><span class="sxs-lookup"><span data-stu-id="7efef-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7efef-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span><span class="sxs-lookup"><span data-stu-id="7efef-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="7efef-129">Cela permet aux applications de s’exécuter dans Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="7efef-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7efef-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7efef-130">See also</span></span>

- [<span data-ttu-id="7efef-131">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7efef-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7efef-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7efef-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
