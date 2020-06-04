---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 633b457106203e213f5d30003e576b7e8132f4d2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400485"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="82055-102">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82055-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="82055-103">Fait en sorte que le compilateur rende les informations de type dans les assemblys spécifiés disponibles pour le projet en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="82055-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82055-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82055-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="82055-105">ou</span><span class="sxs-lookup"><span data-stu-id="82055-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="82055-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="82055-106">Arguments</span></span>  
  
|<span data-ttu-id="82055-107">Terme</span><span class="sxs-lookup"><span data-stu-id="82055-107">Term</span></span>|<span data-ttu-id="82055-108">Définition</span><span class="sxs-lookup"><span data-stu-id="82055-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="82055-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="82055-109">Required.</span></span> <span data-ttu-id="82055-110">Liste délimitée par des virgules des noms de fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="82055-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="82055-111">Si le nom de fichier contient un espace, placez-le entre des guillemets.</span><span class="sxs-lookup"><span data-stu-id="82055-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82055-112">Notes</span><span class="sxs-lookup"><span data-stu-id="82055-112">Remarks</span></span>  
 <span data-ttu-id="82055-113">Le ou les fichiers que vous importez doivent contenir des métadonnées d’assembly.</span><span class="sxs-lookup"><span data-stu-id="82055-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="82055-114">Seuls les types publics sont visibles à l’extérieur de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="82055-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="82055-115">L’option [-addmodule](addmodule.md) importe les métadonnées d’un module.</span><span class="sxs-lookup"><span data-stu-id="82055-115">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="82055-116">Si vous référencez un assembly (assembly A) qui référence lui-même un autre assembly (assembly B), vous devez référencer l’assembly B si :</span><span class="sxs-lookup"><span data-stu-id="82055-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="82055-117">Un type de l’Assembly A hérite d’un type ou implémente une interface de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="82055-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="82055-118">Un champ, une propriété, un événement ou une méthode qui a un type de retour ou un type de paramètre de l’Assembly B est appelé.</span><span class="sxs-lookup"><span data-stu-id="82055-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="82055-119">Utilisez [-LIBPATH](libpath.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="82055-119">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="82055-120">Pour que le compilateur reconnaisse un type dans un assembly (et non un module), il doit être forcé de résoudre le type.</span><span class="sxs-lookup"><span data-stu-id="82055-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="82055-121">Vous pouvez, par exemple, définir une instance du type.</span><span class="sxs-lookup"><span data-stu-id="82055-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="82055-122">D’autres méthodes sont disponibles pour résoudre les noms de types dans un assembly pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="82055-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="82055-123">Par exemple, si vous héritez d’un type dans un assembly, le nom de type devient alors connu du compilateur.</span><span class="sxs-lookup"><span data-stu-id="82055-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="82055-124">Le fichier réponse Vbc. rsp, qui référence les assemblys couramment utilisés .NET Framework, est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="82055-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="82055-125">Utilisez `-noconfig` si vous ne souhaitez pas que le compilateur utilise vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="82055-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="82055-126">La forme abrégée de `-reference` est `-r`.</span><span class="sxs-lookup"><span data-stu-id="82055-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82055-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="82055-127">Example</span></span>  
 <span data-ttu-id="82055-128">La commande suivante compile le fichier source `Input.vb` et les assemblys de référence à partir de `Metad1.dll` et `Metad2.dll` pour produire `Out.exe` .</span><span class="sxs-lookup"><span data-stu-id="82055-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="82055-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82055-129">See also</span></span>

- [<span data-ttu-id="82055-130">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82055-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="82055-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="82055-131">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="82055-132">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82055-132">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="82055-133">Public</span><span class="sxs-lookup"><span data-stu-id="82055-133">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="82055-134">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="82055-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
