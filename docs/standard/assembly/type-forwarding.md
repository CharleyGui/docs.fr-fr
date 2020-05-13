---
title: Transfert de type dans le Common Language Runtime
description: Le transfert de type vous permet de déplacer un type vers un autre assembly .NET sans avoir à recompiler les applications qui utilisent l’assembly d’origine.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f0be61bd4ce88569e22a350a9ea9490d67e74ff3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378598"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Transfert de type dans le Common Language Runtime
Le transfert de type vous permet de déplacer un type vers un autre assembly sans avoir à recompiler les applications utilisant l’assembly d’origine.  
  
 Par exemple, supposons qu’une application utilise la `Example` classe dans un assembly nommé *Utility. dll*. Les développeurs de *Utility. dll* peuvent décider de refactoriser l’assembly et, dans le processus, ils peuvent déplacer la `Example` classe vers un autre assembly. Si l’ancienne version de *Utility. dll* est remplacée par la nouvelle version de *Utility. dll* et son assembly associé, l’application qui utilise la `Example` classe échoue, car elle ne peut pas localiser la `Example` classe dans la nouvelle version de *Utility. dll*.  
  
 Les développeurs de *Utility. dll* peuvent éviter cela en transférant les demandes de la `Example` classe, à l’aide de l' <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribut. Si l’attribut a été appliqué à la nouvelle version de *Utility. dll*, les demandes de la `Example` classe sont transférées à l’assembly qui contient désormais la classe. L’application existante continue à fonctionner normalement, sans nouvelle compilation.  
  
> [!NOTE]
> Dans .NET Framework version 2.0, il est impossible de transférer des types provenant d’assemblys écrits en Visual Basic. Toutefois, une application écrite en Visual Basic peut utiliser des types transférés. Autrement dit, si l’application utilise un assembly codé en C# ou C++ et qu’un type de cet assembly est transmis à un autre assembly, l’application Visual Basic peut utiliser le type transféré.  
  
## <a name="forward-types"></a>Types de transfert  
 Le transfert de type se décompose en quatre étapes :  
  
1. Déplacez le code source associé au type de l’assembly d’origine à l’assembly de destination.  

2. Dans l’assembly où se trouvait le type, ajoutez un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour le type qui a été déplacé. Le code suivant représente l’attribut pour un type nommé `Example` qui a été déplacé.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Compilez l’assembly qui contient désormais le type.  

4. Recompilez l’assembly dans lequel le type se trouvait, avec une référence à l’assembly qui contient désormais le type. Par exemple, si vous compilez un fichier C# à partir de la ligne de commande, utilisez l’option [-Reference (options du compilateur C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) pour spécifier l’assembly qui contient le type. Dans C++, utilisez la directive [#using](/cpp/preprocessor/hash-using-directive-cpp) dans le fichier source pour spécifier l’assembly contenant le type.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Transfert de type (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using directive](/cpp/preprocessor/hash-using-directive-cpp)
