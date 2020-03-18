---
title: Transfert de type dans le Common Language Runtime
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160363"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="5a6e0-102">Transfert de type dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="5a6e0-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="5a6e0-103">Le transfert de type vous permet de déplacer un type vers un autre assembly sans avoir à recompiler les applications utilisant l’assembly d’origine.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="5a6e0-104">Supposons, par exemple, `Example` qu’une application utilise la classe dans un assemblage nommé *Utility.dll*.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="5a6e0-105">Les développeurs de *Utility.dll* pourraient décider de refactor l’assemblage, et dans le processus, ils pourraient déplacer la `Example` classe à un autre assemblage.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="5a6e0-106">Si l’ancienne version de *Utility.dll* est remplacée par la nouvelle version de *Utility.dll* et son assemblage compagnon, l’application qui utilise la `Example` classe échoue parce qu’elle ne peut pas localiser la `Example` classe dans la nouvelle version de *Utility.dll*.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="5a6e0-107">Les développeurs de *Utility.dll* peuvent éviter cela `Example` en transmettant des demandes pour la classe, en utilisant l’attribut. <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute></span><span class="sxs-lookup"><span data-stu-id="5a6e0-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="5a6e0-108">Si l’attribut a été appliqué à la nouvelle version `Example` de *Utility.dll*, les demandes pour la classe sont transmises à l’assemblage qui contient maintenant la classe.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="5a6e0-109">L’application existante continue à fonctionner normalement, sans nouvelle compilation.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a6e0-110">Dans .NET Framework version 2.0, il est impossible de transférer des types provenant d’assemblys écrits en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="5a6e0-111">Toutefois, une application écrite en Visual Basic peut utiliser des types transférés.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="5a6e0-112">Autrement dit, si l’application utilise un assembly codé en C# ou C++ et qu’un type de cet assembly est transmis à un autre assembly, l’application Visual Basic peut utiliser le type transféré.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="5a6e0-113">Types avant</span><span class="sxs-lookup"><span data-stu-id="5a6e0-113">Forward types</span></span>  
 <span data-ttu-id="5a6e0-114">Le transfert de type se décompose en quatre étapes :</span><span class="sxs-lookup"><span data-stu-id="5a6e0-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="5a6e0-115">Déplacez le code source associé au type de l’assembly d’origine à l’assembly de destination.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="5a6e0-116">Dans l’assembly où se trouvait le type, ajoutez un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour le type qui a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="5a6e0-117">Le code suivant représente l’attribut pour un type nommé `Example` qui a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="5a6e0-118">Compilez l’assembly qui contient désormais le type.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-118">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="5a6e0-119">Recompilez l’assembly dans lequel le type se trouvait, avec une référence à l’assembly qui contient désormais le type.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="5a6e0-120">Par exemple, si vous compilez un fichier C à partir de la ligne de commande, utilisez [l’option de référence (options de compilation C)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) pour spécifier l’assemblage qui contient le type.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-120">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="5a6e0-121">Dans C++, utilisez la directive [#using](/cpp/preprocessor/hash-using-directive-cpp) dans le fichier source pour spécifier l’assembly contenant le type.</span><span class="sxs-lookup"><span data-stu-id="5a6e0-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6e0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a6e0-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="5a6e0-123">Type d’end avant (C/CLI)</span><span class="sxs-lookup"><span data-stu-id="5a6e0-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="5a6e0-124">directive #using</span><span class="sxs-lookup"><span data-stu-id="5a6e0-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
