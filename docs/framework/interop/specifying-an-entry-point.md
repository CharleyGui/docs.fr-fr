---
title: Spécification d'un point d'entrée
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: c5f8f735dd3e8c359f88044a532c29303237acc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181311"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="c1901-102">Spécification d'un point d'entrée</span><span class="sxs-lookup"><span data-stu-id="c1901-102">Specifying an Entry Point</span></span>

<span data-ttu-id="c1901-103">Un point d’entrée identifie l’emplacement d’une fonction dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="c1901-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="c1901-104">Dans un projet managé, le nom d’origine ou le point d’entrée ordinal d’une fonction cible identifie cette fonction dans les limites d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="c1901-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="c1901-105">De plus, vous pouvez mapper le point d’entrée à un autre nom pour renommer la fonction de façon plus appropriée.</span><span class="sxs-lookup"><span data-stu-id="c1901-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="c1901-106">La liste suivante répertorie les raisons possibles pour renommer une fonction DLL :</span><span class="sxs-lookup"><span data-stu-id="c1901-106">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="c1901-107">Éviter d’utiliser des noms de fonction API respectant la casse.</span><span class="sxs-lookup"><span data-stu-id="c1901-107">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="c1901-108">Utiliser un nom respectant les conventions de nommage actuelles.</span><span class="sxs-lookup"><span data-stu-id="c1901-108">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="c1901-109">Prendre en charge les fonctions qui acceptent différents types de données (en déclarant plusieurs versions de la même fonction DLL).</span><span class="sxs-lookup"><span data-stu-id="c1901-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="c1901-110">Simplifier l’utilisation des API qui contiennent des versions ANSI et Unicode.</span><span class="sxs-lookup"><span data-stu-id="c1901-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="c1901-111">Cette rubrique montre comment renommer une fonction DLL dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="c1901-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="c1901-112">Renommer une fonction dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1901-112">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="c1901-113">Visual Basic utilise le mot clé **Function** dans l’instruction **Declare** pour définir le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1901-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="c1901-114">L’exemple suivant illustre une déclaration simple.</span><span class="sxs-lookup"><span data-stu-id="c1901-114">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="c1901-115">Vous pouvez remplacer le point d’entrée **MessageBox** par **MsgBox** en incluant le mot clé **Alias** dans votre définition, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c1901-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="c1901-116">Dans les deux exemples, le mot clé **Auto** vous évite de devoir spécifier la version du jeu de caractères pour le point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c1901-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="c1901-117">Pour plus d’informations sur la sélection d’un jeu de caractères, consultez [Spécification d’un jeu de caractères](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="c1901-117">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
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
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="c1901-118">Renommer une fonction dans C# et C++</span><span class="sxs-lookup"><span data-stu-id="c1901-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="c1901-119">Vous pouvez utiliser le champ <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> pour spécifier une fonction DLL à l’aide d’un nom ou d’un ordinal.</span><span class="sxs-lookup"><span data-stu-id="c1901-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="c1901-120">Si le nom de la fonction dans votre définition de méthode est le même que le point d’entrée dans la DLL, vous n’avez pas besoin d’identifier explicitement la fonction à l’aide du champ **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="c1901-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="c1901-121">Sinon, utilisez l’une des formes d’attribut suivantes pour spécifier un nom ou un ordinal :</span><span class="sxs-lookup"><span data-stu-id="c1901-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="c1901-122">Notez que vous devez ajouter le préfixe # (signe dièse) à un ordinal.</span><span class="sxs-lookup"><span data-stu-id="c1901-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="c1901-123">L’exemple suivant montre comment remplacer **MessageBoxA** par **MsgBox** dans votre code à l’aide du champ **EntryPoint**.</span><span class="sxs-lookup"><span data-stu-id="c1901-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
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
  
## <a name="see-also"></a><span data-ttu-id="c1901-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1901-124">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="c1901-125">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="c1901-125">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="c1901-126">Exemples d’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="c1901-126">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="c1901-127">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="c1901-127">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
