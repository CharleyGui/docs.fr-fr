---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 7c013270c8a6b7c2b28f02766df7437b43075dd2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098902"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="2f855-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f855-102">-out (Visual Basic)</span></span>

<span data-ttu-id="2f855-103">Spécifie le nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="2f855-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f855-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f855-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f855-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2f855-105">Arguments</span></span>  
  
|<span data-ttu-id="2f855-106">Terme</span><span class="sxs-lookup"><span data-stu-id="2f855-106">Term</span></span>|<span data-ttu-id="2f855-107">Définition</span><span class="sxs-lookup"><span data-stu-id="2f855-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="2f855-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2f855-108">Required.</span></span> <span data-ttu-id="2f855-109">Nom du fichier de sortie que le compilateur crée.</span><span class="sxs-lookup"><span data-stu-id="2f855-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="2f855-110">Si le nom de fichier contient un espace, mettez-le entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="2f855-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f855-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2f855-111">Remarks</span></span>  

 <span data-ttu-id="2f855-112">Spécifiez le nom complet et l’extension du fichier à créer.</span><span class="sxs-lookup"><span data-stu-id="2f855-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="2f855-113">Si vous ne le faites pas, le fichier. exe utilise son nom dans le fichier de code source contenant la `Sub Main` procédure, et le fichier. dll prend son nom dans le premier fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="2f855-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="2f855-114">Si vous spécifiez un nom de fichier sans extension. exe ou. dll, le compilateur ajoute automatiquement l’extension pour vous, en fonction de la valeur spécifiée pour l' `-target` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="2f855-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="2f855-115">Pour définir l’environnement de développement intégré de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f855-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="2f855-116">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="2f855-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2f855-117">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2f855-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="2f855-118">2. cliquez sur l’onglet **application** .</span><span class="sxs-lookup"><span data-stu-id="2f855-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="2f855-119">3. modifiez la valeur dans la zone nom de l' **assembly** .</span><span class="sxs-lookup"><span data-stu-id="2f855-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2f855-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f855-120">Example</span></span>  

 <span data-ttu-id="2f855-121">Le code suivant compile `T2.vb` et crée le fichier de sortie `T2.exe` .</span><span class="sxs-lookup"><span data-stu-id="2f855-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f855-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f855-122">See also</span></span>

- [<span data-ttu-id="2f855-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f855-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2f855-124">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f855-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="2f855-125">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="2f855-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
