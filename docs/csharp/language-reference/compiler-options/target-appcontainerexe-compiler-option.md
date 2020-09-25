---
description: -target:appcontainerexe (Options du compilateur C#)
title: -target:appcontainerexe (Options du compilateur C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: e4aa60ebc9dcc1a63b63863385b0ee9f13d6d78d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193736"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="cf40b-103">-target:appcontainerexe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="cf40b-103">-target:appcontainerexe (C# Compiler Options)</span></span>

<span data-ttu-id="cf40b-104">Si vous utilisez l’option du compilateur **-target:appcontainerexe**, le compilateur crée un fichier exécutable Windows (.exe) qui doit être exécuté dans un conteneur d’application.</span><span class="sxs-lookup"><span data-stu-id="cf40b-104">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="cf40b-105">Cette option est équivalente à [-target : winexe,](./target-winexe-compiler-option.md) mais elle est conçue pour les applications du Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="cf40b-105">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for Windows 8.x Store apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf40b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf40b-106">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf40b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cf40b-107">Remarks</span></span>  

 <span data-ttu-id="cf40b-108">Pour exiger que l’application s’exécute dans un conteneur d’application, cette option définit un bit dans le fichier [Portable Executable](/windows/desktop/Debug/pe-format) (PE).</span><span class="sxs-lookup"><span data-stu-id="cf40b-108">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="cf40b-109">Lorsque ce bit est défini, une erreur se produit si la méthode CreateProcess tente de lancer l'exécutable en dehors d'un conteneur d'application.</span><span class="sxs-lookup"><span data-stu-id="cf40b-109">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="cf40b-110">À moins que vous utilisiez l’option [-out](./out-compiler-option.md), le fichier de sortie prend le nom du fichier d’entrée qui contient la méthode [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="cf40b-110">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="cf40b-111">Quand vous spécifiez cette option à une invite de commandes, tous les fichiers jusqu’à l’option **-out** ou **-target** suivante sont utilisés pour créer le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="cf40b-111">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="cf40b-112">Pour définir cette option du compilateur dans l'IDE</span><span class="sxs-lookup"><span data-stu-id="cf40b-112">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="cf40b-113">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cf40b-113">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="cf40b-114">Sous l’onglet **Application**, dans la liste **Type de sortie**, choisissez **Application Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="cf40b-114">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="cf40b-115">Cette option est disponible uniquement pour les modèles d’application du Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="cf40b-115">This option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="cf40b-116">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf40b-116">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf40b-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf40b-117">Example</span></span>  

 <span data-ttu-id="cf40b-118">La commande suivante compile `filename.cs` dans un fichier exécutable Windows qui peut être exécuté uniquement dans un conteneur d'application.</span><span class="sxs-lookup"><span data-stu-id="cf40b-118">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf40b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf40b-119">See also</span></span>

- [<span data-ttu-id="cf40b-120">-Target (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="cf40b-120">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="cf40b-121">-target : winexe (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="cf40b-121">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="cf40b-122">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="cf40b-122">C# Compiler Options</span></span>](./index.md)
