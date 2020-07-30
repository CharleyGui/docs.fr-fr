---
title: Comment intercepter une exception non-CLS
description: Découvrez comment intercepter une exception non-CLS. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 255de4cab9a72491eb3b9624d968539d432e0442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302007"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="711c2-104">Comment intercepter une exception non-CLS</span><span class="sxs-lookup"><span data-stu-id="711c2-104">How to catch a non-CLS exception</span></span>
<span data-ttu-id="711c2-105">Certains langages .NET, dont C++/CLI, permettent aux objets de lever des exceptions qui ne dérivent pas d’<xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="711c2-105">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="711c2-106">De telles exceptions sont appelées *exceptions non-CLS* ou *non exceptions*.</span><span class="sxs-lookup"><span data-stu-id="711c2-106">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="711c2-107">Dans C#, vous ne pouvez pas lever d’exceptions non-CLS, mais vous pouvez les intercepter de deux façons :</span><span class="sxs-lookup"><span data-stu-id="711c2-107">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="711c2-108">Dans un bloc `catch (RuntimeWrappedException e)`.</span><span class="sxs-lookup"><span data-stu-id="711c2-108">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="711c2-109">Par défaut, un assembly Visual C# intercepte les exceptions non-CLS comme des exceptions encapsulées.</span><span class="sxs-lookup"><span data-stu-id="711c2-109">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="711c2-110">Utilisez cette méthode si vous devez accéder à l’exception d’origine, qui est accessible via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="711c2-110">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="711c2-111">La procédure située plus loin dans cette rubrique explique comment intercepter les exceptions de cette manière.</span><span class="sxs-lookup"><span data-stu-id="711c2-111">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="711c2-112">Dans un bloc catch général (bloc catch sans type d’exception spécifié) qui est placé après tous les autres blocs `catch`.</span><span class="sxs-lookup"><span data-stu-id="711c2-112">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="711c2-113">Utilisez cette méthode lorsque vous souhaitez effectuer une action (comme écrire dans un fichier journal) en réponse à des exceptions non-CLS, et que vous n’avez pas besoin d’accéder aux informations de l’exception.</span><span class="sxs-lookup"><span data-stu-id="711c2-113">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="711c2-114">Par défaut, le common language runtime inclut dans un wrapper toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="711c2-114">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="711c2-115">Pour désactiver ce comportement, ajoutez cet attribut d’assembly à votre code, généralement dans le fichier AssemblyInfo.cs : `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="711c2-115">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="711c2-116">Comment intercepter une exception non-CLS</span><span class="sxs-lookup"><span data-stu-id="711c2-116">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="711c2-117">Dans un bloc `catch(RuntimeWrappedException e)`, accédez à l’exception d’origine via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="711c2-117">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="711c2-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="711c2-118">Example</span></span>  
 <span data-ttu-id="711c2-119">L’exemple suivant montre comment intercepter une exception non-CLS levée à partir d’une bibliothèque de classes écrite en C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="711c2-119">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="711c2-120">Notez que dans cet exemple, le code client C# sait par avance que le type d’exception levé est un <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="711c2-120">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="711c2-121">Vous pouvez caster la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> en son type d’origine, tant que celui-ci est accessible à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="711c2-121">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="711c2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="711c2-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="711c2-123">Exceptions et gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="711c2-123">Exceptions and Exception Handling</span></span>](./index.md)
