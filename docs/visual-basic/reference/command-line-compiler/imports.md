---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 69781dff1474e42ae5f735fdefd694c6447636b5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085254"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="eb71b-102">-Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb71b-102">-imports (Visual Basic)</span></span>

<span data-ttu-id="eb71b-103">Importe des espaces de noms à partir d’un assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="eb71b-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb71b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb71b-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb71b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="eb71b-105">Arguments</span></span>  
  
|<span data-ttu-id="eb71b-106">Terme</span><span class="sxs-lookup"><span data-stu-id="eb71b-106">Term</span></span>|<span data-ttu-id="eb71b-107">Définition</span><span class="sxs-lookup"><span data-stu-id="eb71b-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="eb71b-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="eb71b-108">Required.</span></span> <span data-ttu-id="eb71b-109">Liste délimitée par des virgules des espaces de noms à importer.</span><span class="sxs-lookup"><span data-stu-id="eb71b-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb71b-110">Notes</span><span class="sxs-lookup"><span data-stu-id="eb71b-110">Remarks</span></span>  

 <span data-ttu-id="eb71b-111">L' `-imports` option importe tout espace de noms défini dans l’ensemble actuel de fichiers sources ou à partir d’un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="eb71b-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="eb71b-112">Les membres d’un espace de noms spécifié avec `-imports` sont disponibles pour tous les fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="eb71b-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="eb71b-113">Utilisez l' [instruction Imports (espace de noms et type .net)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) pour utiliser un espace de noms dans un fichier de code source unique.</span><span class="sxs-lookup"><span data-stu-id="eb71b-113">Use the [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="eb71b-114">Pour définir-Imports dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eb71b-114">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="eb71b-115">1. Sélectionnez un projet dans **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="eb71b-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="eb71b-116">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="eb71b-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="eb71b-117">2. cliquez sur l’onglet **références** .</span><span class="sxs-lookup"><span data-stu-id="eb71b-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="eb71b-118">3. Entrez le nom de l’espace de noms dans la zone en regard du bouton **Ajouter une importation utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="eb71b-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="eb71b-119">4. cliquez sur le bouton **Ajouter une importation d’utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="eb71b-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eb71b-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb71b-120">Example</span></span>  

 <span data-ttu-id="eb71b-121">Le code suivant compile lorsque `-imports:system.globalization` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="eb71b-121">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="eb71b-122">Sans cela, la réussite de la compilation requiert qu’une `Imports System.Globalization` instruction soit incluse au début du fichier de code source, ou que la propriété soit qualifiée complète en tant que `System.Globalization.CultureInfo.CurrentCulture.Name` .</span><span class="sxs-lookup"><span data-stu-id="eb71b-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="eb71b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb71b-123">See also</span></span>

- [<span data-ttu-id="eb71b-124">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb71b-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="eb71b-125">Références et instruction Imports</span><span class="sxs-lookup"><span data-stu-id="eb71b-125">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="eb71b-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="eb71b-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
