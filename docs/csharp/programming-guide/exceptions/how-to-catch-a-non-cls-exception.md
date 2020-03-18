---
title: Comment intercepter une exception non-CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346273"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="e6590-102">Comment intercepter une exception non-CLS</span><span class="sxs-lookup"><span data-stu-id="e6590-102">How to catch a non-CLS exception</span></span>
<span data-ttu-id="e6590-103">Certains langages .NET, dont C++/CLI, permettent aux objets de lever des exceptions qui ne dérivent pas d’<xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="e6590-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="e6590-104">De telles exceptions sont appelées *exceptions non-CLS* ou *non exceptions*.</span><span class="sxs-lookup"><span data-stu-id="e6590-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="e6590-105">Dans C#, vous ne pouvez pas lever d’exceptions non-CLS, mais vous pouvez les intercepter de deux façons :</span><span class="sxs-lookup"><span data-stu-id="e6590-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="e6590-106">Dans un bloc `catch (RuntimeWrappedException e)`.</span><span class="sxs-lookup"><span data-stu-id="e6590-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="e6590-107">Par défaut, un assembly Visual C# intercepte les exceptions non-CLS comme des exceptions encapsulées.</span><span class="sxs-lookup"><span data-stu-id="e6590-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="e6590-108">Utilisez cette méthode si vous devez accéder à l’exception d’origine, qui est accessible via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6590-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e6590-109">La procédure située plus loin dans cette rubrique explique comment intercepter les exceptions de cette manière.</span><span class="sxs-lookup"><span data-stu-id="e6590-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="e6590-110">Dans un bloc catch général (bloc catch sans type d’exception spécifié) qui est placé après tous les autres blocs `catch`.</span><span class="sxs-lookup"><span data-stu-id="e6590-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="e6590-111">Utilisez cette méthode lorsque vous souhaitez effectuer une action (comme écrire dans un fichier journal) en réponse à des exceptions non-CLS, et que vous n’avez pas besoin d’accéder aux informations de l’exception.</span><span class="sxs-lookup"><span data-stu-id="e6590-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="e6590-112">Par défaut, le common language runtime inclut dans un wrapper toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="e6590-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="e6590-113">Pour désactiver ce comportement, ajoutez cet attribut d’assembly à votre code, généralement dans le fichier AssemblyInfo.cs : `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="e6590-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="e6590-114">Comment intercepter une exception non-CLS</span><span class="sxs-lookup"><span data-stu-id="e6590-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="e6590-115">Dans un bloc `catch(RuntimeWrappedException e)`, accédez à l’exception d’origine via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6590-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6590-116"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e6590-116">Example</span></span>  
 <span data-ttu-id="e6590-117">L’exemple suivant montre comment intercepter une exception non-CLS levée à partir d’une bibliothèque de classes écrite en C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="e6590-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="e6590-118">Notez que dans cet exemple, le code client C# sait par avance que le type d’exception levé est un <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6590-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e6590-119">Vous pouvez caster la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> en son type d’origine, tant que celui-ci est accessible à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="e6590-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6590-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6590-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="e6590-121">Exceptions et gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="e6590-121">Exceptions and Exception Handling</span></span>](./index.md)
