---
title: -pdb (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602567"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="73bab-102">-pdb (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="73bab-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="73bab-103">L’option de compilateur **-pdb** spécifie le nom et l’emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="73bab-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73bab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73bab-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="73bab-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="73bab-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="73bab-106">Nom et emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="73bab-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73bab-107">Notes </span><span class="sxs-lookup"><span data-stu-id="73bab-107">Remarks</span></span>  
 <span data-ttu-id="73bab-108">Quand vous spécifiez [-debug (Options du compilateur C#)](./debug-compiler-option.md), le compilateur crée un fichier .pdb dans le même répertoire que celui dans lequel le compilateur va créer le fichier de sortie (.exe ou .dll) avec un nom de fichier identique à celui du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="73bab-108">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="73bab-109">**-pdb** vous permet de spécifier un nom de fichier autre que celui par défaut et un emplacement pour le fichier .pdb.</span><span class="sxs-lookup"><span data-stu-id="73bab-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="73bab-110">Cette option du compilateur ne peut pas être définie dans l’environnement de développement Visual Studio, ni être modifiée par programmation.</span><span class="sxs-lookup"><span data-stu-id="73bab-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73bab-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="73bab-111">Example</span></span>  
 <span data-ttu-id="73bab-112">Compilez `t.cs` et créez un fichier .pdb sous le nom tt.pdb :</span><span class="sxs-lookup"><span data-stu-id="73bab-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="73bab-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73bab-113">See also</span></span>

- [<span data-ttu-id="73bab-114">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="73bab-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="73bab-115">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="73bab-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
