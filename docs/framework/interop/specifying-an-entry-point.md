---
title: Spécification d'un point d'entrée
description: Apprenez à spécifier un point d’entrée, qui identifie l’emplacement d’une fonction dans une DLL. Vous pouvez renommer la fonction en mappant le point d’entrée à un autre nom.
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: a8a45513469c5ee1ec24aae12b02877c9a431513
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99426942"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="60208-104">Spécification d'un point d'entrée</span><span class="sxs-lookup"><span data-stu-id="60208-104">Specifying an Entry Point</span></span>

<span data-ttu-id="60208-105">Un point d’entrée identifie l’emplacement d’une fonction dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="60208-105">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="60208-106">Dans un projet managé, le nom d’origine ou le point d’entrée ordinal d’une fonction cible identifie cette fonction dans les limites d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="60208-106">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="60208-107">De plus, vous pouvez mapper le point d’entrée à un autre nom pour renommer la fonction de façon plus appropriée.</span><span class="sxs-lookup"><span data-stu-id="60208-107">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="60208-108">La liste suivante répertorie les raisons possibles pour renommer une fonction DLL :</span><span class="sxs-lookup"><span data-stu-id="60208-108">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="60208-109">Éviter d’utiliser des noms de fonction API respectant la casse.</span><span class="sxs-lookup"><span data-stu-id="60208-109">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="60208-110">Utiliser un nom respectant les conventions de nommage actuelles.</span><span class="sxs-lookup"><span data-stu-id="60208-110">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="60208-111">Prendre en charge les fonctions qui acceptent différents types de données (en déclarant plusieurs versions de la même fonction DLL).</span><span class="sxs-lookup"><span data-stu-id="60208-111">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="60208-112">Simplifier l’utilisation des API qui contiennent des versions ANSI et Unicode.</span><span class="sxs-lookup"><span data-stu-id="60208-112">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="60208-113">Cette rubrique montre comment renommer une fonction DLL dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="60208-113">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="60208-114">Renommer une fonction dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60208-114">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="60208-115">Visual Basic utilise le mot clé **Function** dans l’instruction **Declare** pour définir le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="60208-115">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="60208-116">L’exemple suivant illustre une déclaration simple.</span><span class="sxs-lookup"><span data-stu-id="60208-116">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="60208-117">Vous pouvez remplacer le point d’entrée **MessageBox** par **MsgBox** en incluant le mot clé **Alias** dans votre définition, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="60208-117">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="60208-118">Dans les deux exemples, le mot clé **Auto** vous évite de devoir spécifier la version du jeu de caractères pour le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="60208-118">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="60208-119">Pour plus d’informations sur la sélection d’un jeu de caractères, consultez [Spécification d’un jeu de caractères](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="60208-119">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="60208-120">Renommer une fonction dans C# et C++</span><span class="sxs-lookup"><span data-stu-id="60208-120">Renaming a Function in C# and C++</span></span>  

 <span data-ttu-id="60208-121">Vous pouvez utiliser le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pour spécifier une fonction DLL à l’aide d’un nom ou d’un ordinal.</span><span class="sxs-lookup"><span data-stu-id="60208-121">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="60208-122">Si le nom de la fonction dans votre définition de méthode est le même que le point d’entrée dans la DLL, vous n’avez pas besoin d’identifier explicitement la fonction à l’aide du champ **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="60208-122">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="60208-123">Sinon, utilisez l’une des formes d’attribut suivantes pour spécifier un nom ou un ordinal :</span><span class="sxs-lookup"><span data-stu-id="60208-123">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="60208-124">Notez que vous devez ajouter le préfixe # (signe dièse) à un ordinal.</span><span class="sxs-lookup"><span data-stu-id="60208-124">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="60208-125">L’exemple suivant montre comment remplacer **MessageBoxA** par **MsgBox** dans votre code à l’aide du champ **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="60208-125">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MsgBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="60208-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60208-126">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="60208-127">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="60208-127">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="60208-128">Exemples d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="60208-128">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="60208-129">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="60208-129">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
