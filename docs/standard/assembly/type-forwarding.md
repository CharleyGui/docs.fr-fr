---
title: Transfert de type dans le Common Language Runtime
description: Le transfert de type vous permet de déplacer un type vers un autre assembly .NET sans avoir à recompiler les applications qui utilisent l’assembly d’origine.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: cd166068993fb5d1a5164615de3926a06dda8098
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687672"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="33a7f-103">Transfert de type dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="33a7f-103">Type forwarding in the common language runtime</span></span>

<span data-ttu-id="33a7f-104">Le transfert de type vous permet de déplacer un type vers un autre assembly sans avoir à recompiler les applications utilisant l’assembly d’origine.</span><span class="sxs-lookup"><span data-stu-id="33a7f-104">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="33a7f-105">Par exemple, supposons qu’une application utilise la `Example` classe dans un assembly nommé *Utility.dll* .</span><span class="sxs-lookup"><span data-stu-id="33a7f-105">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll* .</span></span> <span data-ttu-id="33a7f-106">Les développeurs de *Utility.dll* peuvent décider de refactoriser l’assembly et, dans le processus, ils peuvent déplacer la `Example` classe vers un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="33a7f-106">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="33a7f-107">Si l’ancienne version de *Utility.dll* est remplacée par la nouvelle version de *Utility.dll* et son assembly associé, l’application qui utilise la `Example` classe échoue, car elle ne peut pas localiser la `Example` classe dans la nouvelle version de *Utility.dll* .</span><span class="sxs-lookup"><span data-stu-id="33a7f-107">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll* .</span></span>  
  
 <span data-ttu-id="33a7f-108">Les développeurs de *Utility.dll* peuvent éviter cela en transférant les demandes de la `Example` classe, à l’aide de l' <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="33a7f-108">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="33a7f-109">Si l’attribut a été appliqué à la nouvelle version de *Utility.dll* , les demandes pour la `Example` classe sont transférées à l’assembly qui contient désormais la classe.</span><span class="sxs-lookup"><span data-stu-id="33a7f-109">If the attribute has been applied to the new version of *Utility.dll* , requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="33a7f-110">L’application existante continue à fonctionner normalement, sans nouvelle compilation.</span><span class="sxs-lookup"><span data-stu-id="33a7f-110">The existing application continues to function normally, without recompilation.</span></span>

## <a name="forward-a-type"></a><span data-ttu-id="33a7f-111">Transférer un type</span><span class="sxs-lookup"><span data-stu-id="33a7f-111">Forward a type</span></span>

 <span data-ttu-id="33a7f-112">Le transfert de type se décompose en quatre étapes :</span><span class="sxs-lookup"><span data-stu-id="33a7f-112">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="33a7f-113">Déplacez le code source associé au type de l’assembly d’origine à l’assembly de destination.</span><span class="sxs-lookup"><span data-stu-id="33a7f-113">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="33a7f-114">Dans l’assembly où se trouvait le type, ajoutez un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour le type qui a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="33a7f-114">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="33a7f-115">Le code suivant représente l’attribut pour un type nommé `Example` qui a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="33a7f-115">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="33a7f-116">Compilez l’assembly qui contient désormais le type.</span><span class="sxs-lookup"><span data-stu-id="33a7f-116">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="33a7f-117">Recompilez l’assembly dans lequel le type se trouvait, avec une référence à l’assembly qui contient désormais le type.</span><span class="sxs-lookup"><span data-stu-id="33a7f-117">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="33a7f-118">Par exemple, si vous compilez un fichier C# à partir de la ligne de commande, utilisez l’option [-Reference (options du compilateur C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) pour spécifier l’assembly qui contient le type.</span><span class="sxs-lookup"><span data-stu-id="33a7f-118">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="33a7f-119">Dans C++, utilisez la directive [#using](/cpp/preprocessor/hash-using-directive-cpp) dans le fichier source pour spécifier l’assembly contenant le type.</span><span class="sxs-lookup"><span data-stu-id="33a7f-119">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a7f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33a7f-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="33a7f-121">Transfert de type (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="33a7f-121">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="33a7f-122">#using directive</span><span class="sxs-lookup"><span data-stu-id="33a7f-122">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
