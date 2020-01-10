---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 2a1dd19189ff65413255b9bc137e1a7f0227bbe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716649"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="0f8be-102">-Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f8be-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="0f8be-103">Importe des espaces de noms à partir d’un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f8be-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f8be-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f8be-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f8be-105">Arguments</span></span>  
  
|<span data-ttu-id="0f8be-106">Terme</span><span class="sxs-lookup"><span data-stu-id="0f8be-106">Term</span></span>|<span data-ttu-id="0f8be-107">Définition</span><span class="sxs-lookup"><span data-stu-id="0f8be-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="0f8be-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="0f8be-108">Required.</span></span> <span data-ttu-id="0f8be-109">Liste délimitée par des virgules des espaces de noms à importer.</span><span class="sxs-lookup"><span data-stu-id="0f8be-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f8be-110">Notes</span><span class="sxs-lookup"><span data-stu-id="0f8be-110">Remarks</span></span>  
 <span data-ttu-id="0f8be-111">L’option `-imports` importe tout espace de noms défini dans l’ensemble actuel de fichiers sources ou à partir d’un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="0f8be-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="0f8be-112">Les membres d’un espace de noms spécifié avec `-imports` sont disponibles pour tous les fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="0f8be-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="0f8be-113">Utilisez l' [instruction Imports (espace de noms et type .net)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour utiliser un espace de noms dans un fichier de code source unique.</span><span class="sxs-lookup"><span data-stu-id="0f8be-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="0f8be-114">Pour définir-Imports dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0f8be-114">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0f8be-115">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="0f8be-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0f8be-116">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0f8be-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0f8be-117">2. cliquez sur l’onglet **références** .</span><span class="sxs-lookup"><span data-stu-id="0f8be-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="0f8be-118">3. Entrez le nom de l’espace de noms dans la zone en regard du bouton **Ajouter une importation utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="0f8be-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="0f8be-119">4. cliquez sur le bouton **Ajouter une importation d’utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="0f8be-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f8be-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f8be-120">Example</span></span>  
 <span data-ttu-id="0f8be-121">Le code suivant compile lorsque `-imports:system.globalization` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f8be-121">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="0f8be-122">Sans cela, la réussite de la compilation requiert qu’une instruction `Imports System.Globalization` soit incluse au début du fichier de code source, ou que la propriété soit qualifiée complète comme `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="0f8be-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="0f8be-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f8be-123">See also</span></span>

- [<span data-ttu-id="0f8be-124">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f8be-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0f8be-125">Références et l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="0f8be-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="0f8be-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="0f8be-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
