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
# <a name="how-to-catch-a-non-cls-exception"></a>Comment intercepter une exception non-CLS
Certains langages .NET, dont C++/CLI, permettent aux objets de lever des exceptions qui ne dérivent pas d’<xref:System.Exception>. De telles exceptions sont appelées *exceptions non-CLS* ou *non exceptions*. Dans C#, vous ne pouvez pas lever d’exceptions non-CLS, mais vous pouvez les intercepter de deux façons :  
  
- Dans un bloc `catch (RuntimeWrappedException e)`.
  
     Par défaut, un assembly Visual C# intercepte les exceptions non-CLS comme des exceptions encapsulées. Utilisez cette méthode si vous devez accéder à l’exception d’origine, qui est accessible via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>. La procédure située plus loin dans cette rubrique explique comment intercepter les exceptions de cette manière.  
  
- Dans un bloc catch général (bloc catch sans type d’exception spécifié) qui est placé après tous les autres blocs `catch`.
  
     Utilisez cette méthode lorsque vous souhaitez effectuer une action (comme écrire dans un fichier journal) en réponse à des exceptions non-CLS, et que vous n’avez pas besoin d’accéder aux informations de l’exception. Par défaut, le common language runtime inclut dans un wrapper toutes les exceptions. Pour désactiver ce comportement, ajoutez cet attribut d’assembly à votre code, généralement dans le fichier AssemblyInfo.cs : `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Comment intercepter une exception non-CLS  
  
Dans un bloc `catch(RuntimeWrappedException e)`, accédez à l’exception d’origine via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment intercepter une exception non-CLS levée à partir d’une bibliothèque de classes écrite en C++/CLI. Notez que dans cet exemple, le code client C# sait par avance que le type d’exception levé est un <xref:System.String?displayProperty=nameWithType>. Vous pouvez caster la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> en son type d’origine, tant que celui-ci est accessible à partir de votre code.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [Exceptions et gestion des exceptions](./index.md)
