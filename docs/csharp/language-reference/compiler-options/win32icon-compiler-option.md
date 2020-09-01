---
description: -win32icon (Options du compilateur C#)
title: -win32icon (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 76a54f9011371492bdc15f15c3e40d51082deed3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138408"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="d3bcc-103">-win32icon (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="d3bcc-103">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="d3bcc-104">L’option **-win32icon** insère un fichier .ico dans le fichier de sortie, ce qui lui donne l’apparence souhaitée dans l’Explorateur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-104">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3bcc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3bcc-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3bcc-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d3bcc-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d3bcc-107">Fichier .ico que vous voulez ajouter à votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-107">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3bcc-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="d3bcc-108">Remarks</span></span>  
 <span data-ttu-id="d3bcc-109">Un fichier .ico peut être créé avec le [compilateur de ressources](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="d3bcc-109">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="d3bcc-110">Le compilateur de ressources est appelé quand vous compilez un programme Visual C++ ; un fichier .ico est alors créé à partir du fichier .rc.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-110">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="d3bcc-111">Consultez [-linkresource](./linkresource-compiler-option.md) pour référencer ou [-resource](./resource-compiler-option.md) pour attacher un fichier de ressources .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-111">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="d3bcc-112">Consultez [-win32res](./win32res-compiler-option.md) pour importer un fichier .res.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-112">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d3bcc-113">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d3bcc-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d3bcc-114">Ouvrez les pages **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-114">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="d3bcc-115">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="d3bcc-116">Modifiez la propriété **Icône d’application**.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-116">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="d3bcc-117">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3bcc-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3bcc-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3bcc-118">Example</span></span>  
 <span data-ttu-id="d3bcc-119">Compilez `in.cs` et attachez un fichier .ico `rf.ico` afin de générer le fichier `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="d3bcc-119">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3bcc-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3bcc-120">See also</span></span>

- [<span data-ttu-id="d3bcc-121">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="d3bcc-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d3bcc-122">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="d3bcc-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
