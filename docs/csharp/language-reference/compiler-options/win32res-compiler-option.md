---
description: -win32res (Options du compilateur C#)
title: -win32res (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: c220c78a6d2c3109402a20f0de40fe9665d6c730
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140813"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="27e8b-103">-win32res (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="27e8b-103">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="27e8b-104">L’option **-win32res** insère une ressource Win32 dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="27e8b-104">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e8b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27e8b-105">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="27e8b-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="27e8b-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="27e8b-107">Fichier de ressources que vous voulez ajouter à votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="27e8b-107">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27e8b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="27e8b-108">Remarks</span></span>  
 <span data-ttu-id="27e8b-109">Un fichier de ressources Win32 peut être créé avec le [compilateur de ressources](resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="27e8b-109">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="27e8b-110">Le compilateur de ressources est appelé lorsque vous compilez un programme Visual C++ ; un fichier .res est alors créé à partir du fichier .rc.</span><span class="sxs-lookup"><span data-stu-id="27e8b-110">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="27e8b-111">Une ressource Win32 peut contenir des informations sur la version ou le fichier bitmap (icône) qui permettent d’identifier votre application dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="27e8b-111">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="27e8b-112">Si vous ne spécifiez pas l’option **-win32res**, le compilateur génère des informations de version en fonction de la version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="27e8b-112">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="27e8b-113">Consultez [-linkresource](./linkresource-compiler-option.md) pour référencer ou [-resource](./resource-compiler-option.md) pour attacher un fichier de ressources .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27e8b-113">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="27e8b-114">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="27e8b-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="27e8b-115">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="27e8b-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="27e8b-116">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="27e8b-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="27e8b-117">Cliquez sur le bouton **Fichier de ressources** et choisissez un fichier à l’aide de la zone de liste modifiable.</span><span class="sxs-lookup"><span data-stu-id="27e8b-117">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27e8b-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="27e8b-118">Example</span></span>  
 <span data-ttu-id="27e8b-119">Compilez `in.cs` et attachez un fichier de ressources Win32 `rf.res` afin de générer le fichier `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="27e8b-119">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="27e8b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27e8b-120">See also</span></span>

- [<span data-ttu-id="27e8b-121">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="27e8b-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="27e8b-122">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="27e8b-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
