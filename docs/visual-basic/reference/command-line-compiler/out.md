---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 6b005ac26e3fffad350cb4ce52f7757c9fff2ac1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005331"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="90308-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90308-102">-out (Visual Basic)</span></span>
<span data-ttu-id="90308-103">Spécifie le nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="90308-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90308-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90308-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="90308-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="90308-105">Arguments</span></span>  
  
|<span data-ttu-id="90308-106">Terme</span><span class="sxs-lookup"><span data-stu-id="90308-106">Term</span></span>|<span data-ttu-id="90308-107">Définition</span><span class="sxs-lookup"><span data-stu-id="90308-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="90308-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="90308-108">Required.</span></span> <span data-ttu-id="90308-109">Nom du fichier de sortie que le compilateur crée.</span><span class="sxs-lookup"><span data-stu-id="90308-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="90308-110">Si le nom de fichier contient un espace, mettez-le entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="90308-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90308-111">Notes</span><span class="sxs-lookup"><span data-stu-id="90308-111">Remarks</span></span>  
 <span data-ttu-id="90308-112">Spécifiez le nom complet et l’extension du fichier à créer.</span><span class="sxs-lookup"><span data-stu-id="90308-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="90308-113">Si vous ne le faites pas, le fichier. exe utilise son nom dans le fichier de code source contenant la procédure `Sub Main`, et le fichier. dll prend son nom dans le premier fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="90308-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="90308-114">Si vous spécifiez un nom de fichier sans extension. exe ou. dll, le compilateur ajoute automatiquement l’extension pour vous, en fonction de la valeur spécifiée pour l’option du compilateur `-target`.</span><span class="sxs-lookup"><span data-stu-id="90308-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="90308-115">Pour définir l’environnement de développement intégré de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="90308-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="90308-116">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="90308-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="90308-117">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="90308-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="90308-118">2.  Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="90308-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="90308-119">3.  Modifiez la valeur dans la zone nom de l' **assembly** .</span><span class="sxs-lookup"><span data-stu-id="90308-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="90308-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="90308-120">Example</span></span>  
 <span data-ttu-id="90308-121">Le code suivant compile `T2.vb` et crée le fichier de sortie `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="90308-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="90308-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90308-122">See also</span></span>

- [<span data-ttu-id="90308-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90308-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="90308-124">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90308-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="90308-125">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="90308-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
